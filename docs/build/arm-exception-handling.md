---
description: 'En savoir plus sur : gestion des exceptions ARM'
title: Gestion des exceptions ARM
ms.date: 07/11/2018
ms.assetid: fe0e615f-c033-4ad5-97f4-ff96af45b201
ms.openlocfilehash: 74c915eeee90e0689881621b562f143b7d313941
ms.sourcegitcommit: 6183207b11575d7b44ebd7c18918e916a0d8c63d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97951491"
---
# <a name="arm-exception-handling"></a>Gestion des exceptions ARM

Windows on ARM utilise le même mécanisme de gestion des exceptions structurées pour les exceptions asynchrones générées par le matériel et les exceptions synchrones générées par les logiciels. Les gestionnaires d'exceptions propres aux langages s'appuient sur la gestion des exceptions structurées Windows en utilisant des fonctions d'assistance de langage. Ce document décrit la gestion des exceptions dans Windows on ARM et les applications auxiliaires du langage utilisées par le code généré par l’assembleur Microsoft ARM et le compilateur MSVC.

## <a name="arm-exception-handling"></a>Gestion des exceptions ARM

Windows on ARM utilise des *codes de déroulement* pour contrôler le déroulement de la pile pendant la [gestion structurée des exceptions](/windows/win32/debug/structured-exception-handling) (SEH). Les codes de déroulement sont une séquence d’octets stockés dans la `.xdata` section de l’image exécutable. Ils décrivent le fonctionnement du code de prologue et de épilogue d’une fonction de manière abstraite, de sorte que les effets du prologue d’une fonction peuvent être annulés en préparation du déroulement du frame de pile de l’appelant.

L'interface EABI (Embedded Application Binary Interface) ARM spécifie un modèle de déroulement d'exception qui utilise les codes de déroulement, mais cela n'est pas suffisant pour le déroulement SEH dans Windows, qui doit gérer les cas asynchrones où le processeur se situe au milieu du prologue ou de l'épilogue d'une fonction. De même, Windows sépare le contrôle du déroulement en déroulement au niveau de la fonction et en déroulement de portée propre au langage, qui est unifié dans l'interface EABI ARM. Pour ces raisons, Windows on ARM spécifie plus de détails pour les données et la procédure de déroulement.

### <a name="assumptions"></a>Hypothèses

Les images exécutables pour Windows on ARM utilisent le format PE (Portable Executable). Pour plus d’informations, consultez [format PE](/windows/win32/debug/pe-format). Les informations de gestion des exceptions sont stockées dans les `.pdata` `.xdata` sections et de l’image.

Le mécanisme de gestion des exceptions établit certaines hypothèses concernant le code qui suit l'interface ABI pour Windows on ARM :

- Quand une exception se produit dans le corps d’une fonction, il n’est pas important de savoir si les opérations du prologue sont annulées ou si les opérations du épilogue sont effectuées de manière anticipée. Les deux doivent produire des résultats identiques.

- Les prologues et les épilogues ont tendance à se ressembler. Cela permet de réduire la taille des métadonnées nécessaires à la description du déroulement.

- Les fonctions ont tendance à être relativement petites. Plusieurs optimisations ont besoin de cela pour compresser efficacement les données.

- Si une condition est définie dans un épilogue, elle s'applique également à chaque instruction de l'épilogue.

- Si le pointeur de pile (SP) est enregistré dans un autre registre du prologue, ce registre soit rester inchangé tant que la fonction n'est pas terminée pour permettre au SP d'origine d'être rétabli à tout moment.

- À moins que le SP soit enregistré dans un autre registre, toutes les manipulations dont il fait l'objet doivent se produire exclusivement dans le prologue et l'épilogue.

- Pour dérouler un frame de pile, les opérations suivantes sont nécessaires :

  - ajuster le registre r13 (SP) par incréments de 4 octets ;

  - exécuter un pop sur un ou plusieurs registres d'entiers ;

  - exécuter un pop sur un ou plusieurs registres VFP (virgule flottante vectorielle) ;

  - copier une valeur de registre arbitraire dans le registre r13 (SP) ;

  - charger le pointeur de pile (SP) à partir de la pile à l'aide d'une opération de légère post-décrémentation ;

  - analyser l'un des quelques types de frame bien définis.

### <a name="pdata-records"></a>`.pdata` Documents

Les `.pdata` enregistrements d’une image au format PE sont un tableau ordonné d’éléments de longueur fixe qui décrivent chaque fonction de manipulation de pile. Les fonctions feuilles, qui sont des fonctions qui n’appellent pas d’autres fonctions, ne nécessitent pas d' `.pdata` enregistrement quand elles ne manipulent pas la pile. (Autrement dit, elles n'ont besoin ni de stockage local ni d'enregistrer ou restaurer des registres non volatils.) Les enregistrements de ces fonctions peuvent être omis dans la `.pdata` section pour économiser de l’espace. Une opération de déroulement de l'une de ces fonctions peut simplement copier l'adresse de retour du registre de liaison (ou LR, Link Register) dans le compteur de programme (ou PC, Program Counter) à déplacer vers l'appelant.

Chaque `.pdata` enregistrement pour ARM a une longueur de 8 octets. Le format général d’un enregistrement place l’adresse virtuelle relative (RVA) de la fonction Start dans le premier mot de 32 bits, suivi d’un second mot qui contient soit un pointeur vers un bloc de longueur variable `.xdata` , soit un mot compressé qui décrit une séquence de déroulement de fonction canonique, comme indiqué dans le tableau suivant :

|Décalage de mot|Bits|Objectif|
|-----------------|----------|-------------|
|0|0-31|*`Function Start RVA`* est l’adresse RVA 32 bits du début de la fonction. Si la fonction contient du code thumb, le bit inférieur de cette adresse doit être défini.|
|1|0-1|*`Flag`* est un champ de 2 bits qui indique comment interpréter les 30 bits restants du deuxième `.pdata` mot. Si *`Flag`* a la valeur 0, les bits restants forment un *RVA d’informations sur l’exception* (avec les deux bits de poids faible implicitement 0). Si *`Flag`* est différent de zéro, les bits restants forment une structure de *données de déroulement compressées* .|
|1|2-31|*Informations d’exception RVA* ou *données de déroulement compressées*.<br /><br /> Les *informations d’exception RVA* sont l’adresse de la structure d’informations d’exception de longueur variable, stockée dans la `.xdata` section. Ces données doivent être alignées sur 4 octets.<br /><br /> Les *données de déroulement* compressées sont une description compressée des opérations requises pour se dérouler à partir d’une fonction, en supposant une forme canonique. Dans ce cas, aucun `.xdata` enregistrement n’est requis.|

### <a name="packed-unwind-data"></a>Données de déroulement compressées

Pour les fonctions dont les prologues et les épilogues suivent la forme canonique décrite ci-dessous, il est possible d'utiliser des données de déroulement compressées. Cela élimine la nécessité d’un `.xdata` enregistrement et réduit considérablement l’espace requis pour fournir les données de déroulement. Les prologues et épilogues canoniques visent à répondre aux besoins courants d'une fonction simple qui ne nécessite pas de gestionnaire d'exceptions et qui effectue ses opérations de configuration et de démontage dans un ordre normal.

Ce tableau montre le format d’un `.pdata` enregistrement qui contient des données de déroulement compressées :

|Décalage de mot|Bits|Objectif|
|-----------------|----------|-------------|
|0|0-31|*`Function Start RVA`* est l’adresse RVA 32 bits du début de la fonction. Si la fonction contient du code thumb, le bit inférieur de cette adresse doit être défini.|
|1|0-1|*`Flag`* est un champ de 2 bits qui a les significations suivantes :<br /><br />-00 = données de déroulement compressées non utilisées ; point des bits restants à `.xdata` Enregistrer.<br />-01 = données de déroulement compressées.<br />-10 = données de déroulement compressées pour lesquelles la fonction est supposée ne pas avoir de prologue. Ceci est utile pour décrire les fragments de fonction discontinus par rapport au début de la fonction.<br />-11 = réservé.|
|1|2-12|*`Function Length`* est un champ de 11 bits qui fournit la longueur de la fonction entière en octets divisée par 2. Si la fonction est supérieure à 4 Ko, un `.xdata` enregistrement complet doit être utilisé à la place.|
|1|13-14|*`Ret`* est un champ de 2 bits qui indique le mode de retour de la fonction :<br /><br />-00 = retour via pop {PC} (le *`L`* bit de l’indicateur doit être défini sur 1 dans ce cas).<br />-01 = Retour à l’aide d’une branche 16 bits.<br />-10 = retour à l’aide d’une branche 32 bits.<br />-11 = aucun épilogue. Ceci est utile pour décrire un fragment de fonction discontinu qui peut ne contenir qu'un prologue, mais dont l'épilogue se trouve ailleurs.|
|1|15|*`H`* est un indicateur de 1 bit qui indique si la fonction « maisons » les registres de paramètres entiers (R0-R3) en les envoyant au début de la fonction et libère les 16 octets de la pile avant de retourner. (0 = n'héberge pas les registres, 1 = héberge les registres.)|
|1|16-18|*`Reg`* est un champ de 3 bits qui indique l’index du dernier Registre non volatile enregistré. Si le *`R`* bit est 0, seuls les registres d’entiers sont enregistrés et sont supposés être dans la plage de R4-RN, où N est égal à 4 + *`Reg`* . Si le *`R`* bit a la valeur 1, seuls les registres à virgule flottante sont enregistrés et sont supposés être dans la plage de D8-DN, où N est égal à 8 + *`Reg`* . La combinaison spéciale de *`R`* = 1 et *`Reg`* = 7 indique qu’aucun registre n’est enregistré.|
|1|19|*`R`* est un indicateur de 1 bit qui indique si les registres non volatiles enregistrés sont des registres d’entiers (0) ou des registres à virgule flottante (1). Si *`R`* a la valeur 1 et que le *`Reg`* champ a la valeur 7, aucun registre non volatil n’a fait l’objet d’un push.|
|1|20|*`L`* est un indicateur de 1 bit qui indique si la fonction enregistre/restaure la valeur LR, ainsi que les autres registres indiqués par le *`Reg`* champ. (0 = n'enregistre/ne restaure pas, 1 = enregistre/restaure.)|
|1|21|*`C`* est un indicateur de 1 bit qui indique si la fonction comprend des instructions supplémentaires pour configurer une chaîne de frames pour le parcours de pile rapide (1) ou non (0). Si ce bit est défini, le registre r11 est ajouté implicitement à la liste des registres non volatils d'entiers enregistrés. (Voir les restrictions ci-dessous si l' *`C`* indicateur est utilisé.)|
|1|22-31|*`Stack Adjust`* est un champ de 10 bits qui indique le nombre d’octets de la pile alloués pour cette fonction, divisé par 4. Cependant, seules les valeurs comprises entre 0x000 et 0x3F3 peuvent être directement encodées. Les fonctions qui allouent plus de 4044 octets de pile doivent utiliser un `.xdata` enregistrement complet. Si le *`Stack Adjust`* champ est égal à 0x3f4 ou supérieur, les 4 bits de poids faible ont une signification particulière :<br /><br />-Bits 0-1 indiquent le nombre de mots de l’ajustement de pile (1-4) moins 1.<br />-Le bit 2 a la valeur 1 si le prologue a combiné cet ajustement dans son opération push.<br />-Bit 3 a la valeur 1 si le épilogue a combiné cet ajustement dans son opération pop.|

Du fait des redondances possibles dans les encodages précédents, les restrictions suivantes s'appliquent :

- Si l' *`C`* indicateur a la valeur 1 :

  - L' *`L`* indicateur doit également avoir la valeur 1, car la chaîne de frames exige à la fois R11 et LR.

  - R11 ne doit pas être inclus dans l’ensemble de registres décrit par *`Reg`* . Autrement dit, si R4-R11 fait l’objet d’un push, *`Reg`* doit uniquement décrire R4-R10, car l' *`C`* indicateur implique R11.

- Si le *`Ret`* champ a la valeur 0, l' *`L`* indicateur doit avoir la valeur 1.

La violation de ces restrictions donne lieu à une séquence non prise en charge.

Dans le cadre de la discussion ci-dessous, deux Pseudo-indicateurs sont dérivés de *`Stack Adjust`* :

- *`PF`* ou « repli de prologue » indique que *`Stack Adjust`* est égal à 0x3f4 ou supérieur et que le bit 2 est défini.

- *`EF`* ou « épilogue repli » indique que *`Stack Adjust`* est égal à 0x3f4 ou supérieur et que le bit 3 est défini.

Les prologues des fonctions canoniques peuvent avoir jusqu'à 5 instructions (à noter que les instructions 3a et 3b s'excluent mutuellement) :

|Instruction|Un opcode est considéré être présent si :|Taille|Opcode|Codes de déroulement|
|-----------------|-----------------------------------|----------|------------|------------------|
|1|*`H`*= = 1|16|`push {r0-r3}`|04|
|2|*`C`*= = 1 ou *`L`* = = 1 ou *`R`* = = 0 ou *`PF`* = = 1|16/32|`push {registers}`|80-BF/D0-DF/EC-ED|
|3a|*`C`*= = 1 et ( *`L`* = = 0 et *`R`* = = 1 et *`PF`* = = 0)|16|`mov r11,sp`|C0-CF/FB|
|3b|*`C`*= = 1 et ( *`L`* = = 1 ou *`R`* = = 0 ou *`PF`* = = 1)|32|`add r11,sp,#xx`|FC|
|4|*`R`*= = 1 et *`Reg`* ! = 7|32|`vpush {d8-dE}`|E0-E7|
|5|*`Stack Adjust`* ! = 0 et *`PF`* = = 0|16/32|`sub sp,sp,#xx`|00-7F/E8-EB|

L’instruction 1 est toujours présente si le *`H`* bit a la valeur 1.

Pour configurer le chaînage de frames, l’instruction 3A ou 3b est présente si le *`C`* bit est défini. Il s'agit d'un `mov` de 16 bits si aucun autre registre que r11 et LR ne fait l'objet d'un push ; sinon, il s'agit d'un `add` de 32 bits.

Si un ajustement non plié est spécifié, l'instruction 5 est l'ajustement de pile explicite.

Les instructions 2 et 4 sont définies selon qu'un push est nécessaire ou pas. Ce tableau récapitule les registres enregistrés en fonction des *`C`* *`L`* champs,, *`R`* et *`PF`* . Dans tous les cas, *`N`* est égal à *`Reg`* + 4, *`E`* est égal à *`Reg`* + 8, et *`S`* est égal à (~ *`Stack Adjust`* ) & 3.

|C|L|R|PF|Registres d'entiers faisant l'objet d'un push|Registres VFP faisant l'objet d'un push|
|-------|-------|-------|--------|------------------------------|--------------------------|
|0|0|0|0|R4-r *`N`*|aucun|
|0|0|0|1|r *`S`* -r *`N`*|aucun|
|0|0|1|0|Aucun|D8-d *`E`*|
|0|0|1|1|r *`S`* -R3|D8-d *`E`*|
|0|1|0|0|R4-r *`N`* , LR|aucun|
|0|1|0|1|r *`S`* -r *`N`* , LR|aucun|
|0|1|1|0|LR|D8-d *`E`*|
|0|1|1|1|r *`S`* -R3, LR|D8-d *`E`*|
|1|0|0|0|R4-r *`N`* , R11|aucun|
|1|0|0|1|r *`S`* -r *`N`* , R11|aucun|
|1|0|1|0|r11|D8-d *`E`*|
|1|0|1|1|r *`S`* -R3, R11|D8-d *`E`*|
|1|1|0|0|R4-r *`N`* , R11, LR|aucun|
|1|1|0|1|r *`S`* -r *`N`* , R11, LR|aucun|
|1|1|1|0|r11, LR|D8-d *`E`*|
|1|1|1|1|r *`S`* -R3, R11, LR|D8-d *`E`*|

Les épilogues des fonctions canoniques suivent une forme analogue, mais en sens inverse et avec quelques options supplémentaires. L'épilogue peut compter jusqu'à 5 instructions et sa forme est strictement dictée par celle du prologue.

|Instruction|Un opcode est considéré être présent si :|Taille|Opcode|
|-----------------|-----------------------------------|----------|------------|
|6|*`Stack Adjust`*! = 0 et *`EF`* = = 0|16/32|`add   sp,sp,#xx`|
|7|*`R`*= = 1 et *`Reg`* ! = 7|32|`vpop  {d8-dE}`|
|8|*`C`*= = 1 ou ( *`L`* = = 1 et *`H`* = = 0) ou *`R`* = = 0 ou *`EF`* = = 1|16/32|`pop   {registers}`|
|9a|*`H`*= = 1 et *`L`* = = 0|16|`add   sp,sp,#0x10`|
|9b|*`H`*= = 1 et *`L`* = = 1|32|`ldr   pc,[sp],#0x14`|
|10a|*`Ret`*= = 1|16|`bx    reg`|
|10b|*`Ret`*= = 2|32|`b     address`|

L’instruction 6 est l’ajustement de pile explicite si un ajustement non plié est spécifié. Étant donné que *`PF`* est indépendant de *`EF`* , il est possible que l’instruction 5 soit présente sans l’instruction 6, ou vice-versa.

Les instructions 7 et 8 utilisent la même logique que le prologue pour déterminer quels registres sont restaurés à partir de la pile, mais avec ces deux modifications : tout d’abord, *`EF`* est utilisé à la place de *`PF`* ; second, si *`Ret`* = 0, LR est remplacé par PC dans la liste de registres et le épilogue se termine immédiatement.

Si *`H`* est défini, l’instruction 9A ou 9B est présente. L’instruction 9A est utilisée lorsque *`L`* a la valeur 0, pour indiquer que la valeur LR n’est pas sur la pile. Dans ce cas, la pile est ajustée manuellement et *`Ret`* doit avoir la valeur 1 ou 2 pour spécifier un retour explicite. L’instruction 9B est utilisée lorsque *`L`* a la valeur 1, pour indiquer une fin précoce au épilogue, et pour retourner et ajuster la pile en même temps.

Si le épilogue n’est pas déjà terminé, l’instruction 10A ou 10 est présente, pour indiquer une branche 16 bits ou 32 bits, en fonction de la valeur de *`Ret`* .

### <a name="xdata-records"></a>`.xdata` Documents

Lorsque le format compressé est insuffisant pour décrire le déroulement d’une fonction, vous devez créer un enregistrement de longueur variable `.xdata` . L’adresse de cet enregistrement est stockée dans le deuxième mot de l' `.pdata` enregistrement. Le format de `.xdata` est un ensemble de mots de longueur variable condensé qui comporte quatre sections :

1. En-tête 1 ou 2-Word qui décrit la taille globale de la `.xdata` structure et fournit les données de fonction clés. Le deuxième mot est présent uniquement si les champs *nombre épilogue* et *mots de code* ont tous les deux la valeur 0. Les champs sont décrits en détail dans ce tableau :

   |Word|Bits|Objectif|
   |----------|----------|-------------|
   |0|0-17|*`Function Length`* est un champ de 18 bits qui indique la longueur totale de la fonction en octets, divisée par 2. Si une fonction est supérieure à 512 Ko, plusieurs `.pdata` enregistrements et `.xdata` doivent être utilisés pour décrire la fonction. Pour plus de détails, consultez la section Grandes fonctions dans ce document.|
   |0|18-19|*Vers* est un champ de 2 bits qui décrit la version restante `.xdata` . Seule la version 0 est actuellement définie ; les valeurs 1 à 3 sont réservées.|
   |0|20|*X* est un champ de 1 bit qui indique la présence (1) ou l’absence (0) de données d’exception.|
   |0|21|*`E`* est un champ de 1 bit qui indique que les informations qui décrivent un seul épilogue sont empaquetées dans l’en-tête (1) au lieu d’exiger des mots d’étendue supplémentaires plus tard (0).|
   |0|22|*F* est un champ de 1 bit qui indique que cet enregistrement décrit un fragment de fonction (1) ou une fonction complète (0). Un fragment implique l'absence de prologue et que tout le traitement des prologues doit être ignoré.|
   |0|23-27|Le *nombre de épilogue* est un champ de 5 bits qui a deux significations, en fonction de l’état du *`E`* bit :<br /><br /> -Si *`E`* a la valeur 0, ce champ est le nombre total d’étendues d’exception décrites dans la section 3. S’il existe plus de 31 portées dans la fonction, ce champ et le champ *code Word* doivent tous deux avoir la valeur 0 pour indiquer qu’un mot d’extension est nécessaire.<br />-Si *`E`* est 1, ce champ spécifie l’index du premier code de déroulement qui décrit le seul épilogue.|
   |0|28-31|Les *mots de code* sont un champ de 4 bits qui spécifie le nombre de mots de 32 bits requis pour contenir tous les codes de déroulement de la section 4. Si plus de 15 mots sont requis pour plus de 63 octets de code de déroulement, ce champ et le champ *épilogue Count* doivent tous deux avoir la valeur 0 pour indiquer qu’un mot d’extension est nécessaire.|
   |1|0-15|Le *nombre de épilogue étendus* est un champ de 16 bits qui fournit plus d’espace pour l’encodage d’un nombre anormalement élevé de épilogues. Le mot d’extension qui contient ce champ n’est présent que si les champs *épilogue Count* et *code* Words dans le premier mot d’en-tête ont tous les deux la valeur 0.|
   |1|16-23|Les *mots de code étendus* sont un champ de 8 bits qui fournit plus d’espace pour l’encodage d’un nombre anormalement élevé de mots de code de déroulement. Le mot d’extension qui contient ce champ n’est présent que si les champs *épilogue Count* et *code* Words dans le premier mot d’en-tête ont tous les deux la valeur 0.|
   |1|24-31|Réservé|

1. Une fois les données d’exception (si le *`E`* bit dans l’en-tête a la valeur 0), une liste d’informations sur les étendues de épilogue, qui sont empaquetées dans un mot et stockées dans l’ordre de l’offset de début d’incrémentation. Chaque portée contient ces champs :

   |Bits|Objectif|
   |----------|-------------|
   |0-17|*Épilogue Start offset* est un champ de 18 bits qui décrit le décalage de épilogue, en octets divisé par 2, par rapport au début de la fonction.|
   |18-19|*Res* est un champ de 2 bits réservé pour une future expansion. Il doit avoir la valeur 0.|
   |20-23|La *condition* est un champ de 4 bits qui donne la condition sous laquelle le épilogue est exécuté. Pour les épilogues inconditionnels, il doit avoir la valeur 0xE, ce qui indique « toujours ». (Un épilogue doit être entièrement conditionnel ou entièrement inconditionnel, et en mode Thumb-2, l'épilogue commence par la première instruction située après l'opcode IT.)|
   |24-31|*Épilogue Start index* est un champ de 8 bits qui indique l’index d’octet du premier code de déroulement qui décrit ce épilogue.|

1. Après la liste des portées d'épilogue figure un tableau d'octets qui contient les codes de déroulement, qui sont décrits en détail dans la section Code de déroulement de cet article. Ce tableau est rempli à la fin jusqu'à la limite du mot complet le plus proche. Les octets sont stockés dans un ordre Little-Endian, ce qui permet de les récupérer directement en mode Little-Endian.

1. Si le champ *X* dans l’en-tête est 1, les octets de code de déroulement sont suivis par les informations du gestionnaire d’exceptions. Cela se compose d’un *RVA de gestionnaire d’exceptions* qui contient l’adresse du gestionnaire d’exceptions, suivi immédiatement de la quantité de données (de longueur variable) requise par le gestionnaire d’exceptions.

L' `.xdata` enregistrement est conçu de sorte qu’il est possible de récupérer les 8 premiers octets et de calculer la taille complète de l’enregistrement, à l’exclusion de la longueur des données d’exception de taille variable qui suivent. Cet extrait de code permet de calculer la taille de l'enregistrement :

```cpp
ULONG Comput`.xdata`Size(PULONG `.xdata`)
{
    ULONG EpilogueScopes;
    ULONG Size;
    ULONG UnwindWords;

    if (`.xdata`[0] >> 23) != 0) {
        Size = 4;
        EpilogueScopes = `.xdata`[0] >> 23) & 0x1f;
        UnwindWords = `.xdata`[0] >> 28) & 0x0f;
    } else {
        Size = 8;
        EpilogueScopes =`.xdata`[1] & 0xffff;
        UnwindWords = `.xdata`[1] >> 16) & 0xff;
    }

    if (!`.xdata`[0] & (1 << 21))) {
        Size += 4 * EpilogueScopes;
    }
    Size += 4 * UnwindWords;
    if `.xdata`[0] & (1 << 20)) {
        Size += 4;
    }
    return Size;
}
```

Bien que le prologue et chaque épilogue possèdent un index dans les codes de déroulement, la table est partagée entre eux. Il n'est pas rare qu'ils puissent tous partager les mêmes codes de déroulement. Nous recommandons aux rédacteurs de compilateur de prévoir une optimisation pour ce cas de figure, car la taille maximale d'index est de 255, ce qui limite le nombre total de codes de déroulement possibles pour une fonction déterminée.

### <a name="unwind-codes"></a>Codes de déroulement

Le tableau de codes de déroulement est un pool de séquences d'instructions qui indiquent exactement comment annuler les effets du prologue, dans l'ordre où les opérations doivent être annulées. Les codes de déroulement correspondent à un mini-ensemble d'instructions, encodé sous la forme d'une chaîne d'octets. Une fois l'exécution terminée, l'adresse de retour vers la fonction appelante se trouve dans le registre LR, et tous les registres non volatils sont restaurés avec les valeurs qui étaient les leurs au moment où la fonction a été appelée.

S'il était garanti que les exceptions ne se produisaient que dans le corps d'une fonction et jamais dans un prologue ou un épilogue, une seule séquence de déroulement serait nécessaire. Cependant, le modèle de déroulement Windows impose de pouvoir effectuer un déroulement à partir d'un prologue ou d'un épilogue partiellement exécuté. Pour satisfaire cette exigence, les codes de déroulement ont été soigneusement conçus pour bénéficier d'un mappage un-à-un non équivoque à chaque opcode approprié dans le prologue et l'épilogue. Cela a plusieurs conséquences :

- Il est possible de calculer la longueur du prologue et de l'épilogue en comptant le nombre de codes de déroulement. Cela est possible même avec des instructions Thumb-2 de longueur variable, car il existe des mappages distincts pour les opcodes de 16 et 32 bits.

- En comptant le nombre d'instructions après le début d'une portée d'épilogue, il est possible d'ignorer le nombre équivalent de codes de déroulement et d'exécuter le reste d'une séquence pour terminer le déroulement partiellement exécuté par l'épilogue.

- En comptant le nombre d'instructions avant la fin du prologue, il est possible d'ignorer le nombre équivalent de codes de déroulement et d'exécuter le reste d'une séquence pour annuler uniquement les parties du prologue qui ont mené à bien l'exécution.

Le tableau suivant présente le mappage entre les codes de déroulement et les opcodes. Les codes les plus courants ne font qu'un octet, alors que les moins courants nécessitent deux, trois, voire quatre octets. Chaque code est stocké de l'octet le plus significatif à l'octet le moins significatif. La structure des codes de déroulement est différente de l'encodage décrit dans l'interface EABI ARM, car ces codes de déroulement sont conçus pour bénéficier d'un mappage un-à-un aux opcodes dans le prologue et l'épilogue afin de permettre le déroulement des prologues et épilogues partiellement exécutés.

|Octet 1|Octet 2|Octet 3|Octet 4|Taille d'opcode|Explication|
|------------|------------|------------|------------|------------|-----------------|
|00-7F||||16|`add   sp,sp,#X`<br /><br /> où X correspond à (code & 0x7F) \* 4|
|80-BF|00-FF|||32|`pop   {r0-r12, lr}`<br /><br /> où LR est dépilé si le code & 0x2000 et R0-R12 sont dépilés si le bit correspondant est défini dans le code & 0x1FFF|
|C0-CF||||16|`mov   sp,rX`<br /><br /> où X correspond au code & 0x0F|
|D0-D7||||16|`pop   {r4-rX,lr}`<br /><br /> où X correspond à (code & 0x03) + 4 et LR est dépilé si le code & 0x04|
|D8-DF||||32|`pop   {r4-rX,lr}`<br /><br /> où X correspond à (code & 0x03) + 8 et LR est dépilé si le code & 0x04|
|E0-E7||||32|`vpop  {d8-dX}`<br /><br /> où X correspond à (code & 0x07) + 8|
|E8-EB|00-FF|||32|`addw  sp,sp,#X`<br /><br /> où X correspond à (code & 0x03FF) \* 4|
|EC-ED|00-FF|||16|`pop   {r0-r7,lr}`<br /><br /> où LR est dépilé si le code & 0x0100 et R0-R7 sont dépilés si le bit correspondant est défini dans le code & 0x00FF|
|EE|00-0F|||16|Spécifique à Microsoft|
|EE|10-FF|||16|Disponible|
|EF|00-0F|||32|`ldr   lr,[sp],#X`<br /><br /> où X correspond à (code & 0x000F) \* 4|
|EF|10-FF|||32|Disponible|
|F0-F4||||-|Disponible|
|F5|00-FF|||32|`vpop  {dS-dE}`<br /><br /> où S est (code & 0x00F0)  >> 4 et E est du code & 0x000F|
|F6|00-FF|||32|`vpop  {dS-dE}`<br /><br /> où S est ((code & 0x00F0)  >> 4) + 16 et E est (code & 0x000F) + 16|
|F7|00-FF|00-FF||16|`add   sp,sp,#X`<br /><br /> où X correspond à (code & 0x00FFFF) \* 4|
|F8|00-FF|00-FF|00-FF|16|`add   sp,sp,#X`<br /><br /> où X correspond à (code & 0x00FFFFFF) \* 4|
|F9|00-FF|00-FF||32|`add   sp,sp,#X`<br /><br /> où X correspond à (code & 0x00FFFF) \* 4|
|FA|00-FF|00-FF|00-FF|32|`add   sp,sp,#X`<br /><br /> où X correspond à (code & 0x00FFFFFF) \* 4|
|FB||||16|nop (16 bits)|
|FC||||32|nop (32 bits)|
|FD||||16|fin + nop de 16 bits dans l'épilogue|
|FE||||32|fin + nop de 32 bits dans l'épilogue|
|FF||||-|end|

Cela montre la plage de valeurs hexadécimales pour chaque octet dans un *code* de code de déroulement, ainsi que la taille de l’opcode *Opsize* et l’interprétation de l’instruction d’origine correspondante. Les cellules vides indiquent des codes de déroulement plus courts. Dans les instructions qui contiennent des valeurs élevées couvrant plusieurs octets, les bits les plus significatifs sont stockés en premier. Le champ *Opsize* affiche la taille d’opcode implicite associée à chaque opération Thumb-2. Les entrées en double apparentes figurant dans le tableau avec des encodages différents servent à faire la distinction entre les différentes tailles d’opcode.

Les codes de déroulement sont conçus de telle sorte que le premier octet du code indique à la fois la taille totale en octets du code et la taille de l'opcode correspondant dans le flux d'instructions. Pour calculer la taille du prologue ou de l’épilogue, parcourez les codes de déroulement du début jusqu’à la fin de la séquence, puis utilisez une table de correspondance ou une méthode similaire pour déterminer la longueur de l’opcode correspondant.

Les codes de déroulement 0xFD et 0xFE sont équivalents au code de fin normal 0xFF, mais prennent en compte un opcode nop supplémentaire dans le cas de l'épilogue, de 16 ou 32 bits. Pour les prologues, les codes 0xFD, 0xFE et 0xFF sont tout à fait équivalents. Cela compte pour les fins épilogue courantes `bx lr` ou `b <tailcall-target>` , qui n’ont pas d’instruction de prologue équivalente. Cela augmente les probabilités de partage des séquences de déroulement entre le prologue et les épilogues.

Dans bien des cas, il devrait être possible d'utiliser le même ensemble de codes de déroulement pour le prologue et tous les épilogues. Or, pour gérer le déroulement des prologues et des épilogues partiellement exécutés, il serait nécessaire d'avoir plusieurs séquences de code de déroulement avec un ordre ou un comportement différents. C'est pourquoi chaque épilogue a son propre index dans le tableau de déroulement pour indiquer où commencer l'exécution.

### <a name="unwinding-partial-prologues-and-epilogues"></a>Déroulement des prologues et des épilogues partiels

Le cas de déroulement le plus courant est celui où l'exception se produit dans le corps de la fonction, en dehors du prologue et de tous les épilogues. Dans ce cas, le déchargeur exécute les codes du tableau de déchargement à partir de l'index 0 et continue jusqu'à ce qu'un opcode de fin soit détecté.

Quand une exception se produit pendant l'exécution d'un prologue ou d'un épilogue, le frame de pile n'est que partiellement construit et le déchargeur doit déterminer exactement ce qui a été fait pour l'annuler correctement.

Penchons-nous à titre d'exemple sur cette séquence de prologue et d'épilogue :

```asm
0000:   push  {r0-r3}         ; 0x04
0002:   push  {r4-r9, lr}     ; 0xdd
0006:   mov   r7, sp          ; 0xc7
...
0140:   mov   sp, r7          ; 0xc7
0142:   pop   {r4-r9, lr}     ; 0xdd
0146:   add   sp, sp, #16     ; 0x04
0148:   bx    lr
```

En regard de chaque opcode figure le code déroulement approprié qui décrit l’opération. La séquence de codes de déroulement du prologue est une image miroir des codes de déroulement de l'épilogue, l'instruction finale en moins. Ce cas est courant et est la raison pour laquelle les codes de déroulement du prologue sont toujours supposés être stockés dans l’ordre inverse à partir de l’ordre d’exécution du prologue. Cela nous donne un ensemble commun de codes de déroulement :

```asm
0xc7, 0xdd, 0x04, 0xfd
```

Le code 0xFD est un code spécial pour la fin de la séquence qui signifie que l'épilogue est plus long que le prologue d'une instruction de 16 bits. Cela permet un plus grand partage de codes de déroulement.

Dans l'exemple, si une exception se produit pendant l'exécution du corps de la fonction entre le prologue et l'épilogue, le déroulement commence par le cas de l'épilogue au décalage 0 dans le code de l'épilogue. Cela correspond au décalage 0x140 dans l'exemple. Le dérouleur exécute la séquence de déroulement complète, car aucun nettoyage n'a été fait. En revanche, si l'exception se produit au niveau de la première instruction suivant le début du code de l'épilogue, le dérouleur peut procéder au déroulement en ignorant le premier code de déroulement. Dans le cas d’un mappage un-à-un entre les OpCodes et les codes de déroulement, si le déroulement s’effectue à partir de l’instruction *n* dans le épilogue, le dérouleur doit ignorer les *n* premiers codes de déroulement.

La logique qui prévaut dans le cas du prologue est identique mais inversée. Si le déroulement se produit à partir du décalage 0 dans le prologue, il n'y a rien à exécuter. Si le déroulement démarre à la première instruction, la séquence de déroulement doit commencer au premier code de déroulement en partant de la fin, car les codes de déroulement du prologue sont stockés dans l'ordre inverse. Dans le cas général, si le déroulement à partir de l’instruction *n* dans le prologue, le déroulement doit commencer à s’exécuter aux codes de déroulement *n* à partir de la fin de la liste de codes.

Les codes de déroulement de prologue et d'épilogue ne correspondent pas toujours exactement. Dans ce cas, il se peut que le tableau des codes de déroulement doive contenir plusieurs séquences de codes. Pour déterminer à quel décalage commencer le traitement des codes, suivez cette logique :

1. Si le déroulement démarre dans le corps de la fonction, commencez à exécuter les codes de déroulement à l’index 0 et continuez jusqu’à ce qu’un opcode de fin soit atteint.

2. Si le déroulement démarre dans un épilogue, utilisez l'index de démarrage propre à l'épilogue fourni par la portée de l'épilogue. Calculez le nombre d'octets qui séparent le compteur de programme (PC) du début de l'épilogue. Parcourez les codes de déroulement jusqu'à ce que toutes les instructions déjà exécutées soient prises en compte. Exécutez la séquence de déroulement à partir de ce point.

3. Si le déroulement démarre dans le prologue, partez de l'index 0 dans les codes de déroulement. Calculez la longueur du code de prologue à partir de la séquence, puis calculez le nombre d'octets qui séparent le compteur de programme (PC) de la fin du prologue. Parcourez les codes de déroulement jusqu'à ce que toutes les instructions non exécutées soient prises en compte. Exécutez la séquence de déroulement à partir de ce point.

Les codes de déroulement du prologue doivent toujours être les premiers dans le tableau. Ce sont aussi les codes généralement utilisés dans les déroulements qui démarre dans le corps. Les séquences de codes propres à l'épilogue doivent suivre immédiatement la séquence de codes du prologue.

### <a name="function-fragments"></a>Fragments de fonction

Pour l'optimisation de code, il peut être utile de scinder une fonction en plusieurs parties discontinues. Lorsque cela est fait, chaque fragment de fonction requiert son propre `.pdata` enregistrement distinct (et éventuellement `.xdata` ).

En supposant que le prologue de la fonction se trouve au début de la fonction et qu'il ne peut pas être scindé, il existe quatre cas de fragments de fonction :

- un prologue uniquement ; tous les épilogues se trouvent dans d'autres fragments ;

- un prologue et un ou plusieurs épilogues ; épilogues supplémentaires dans d'autres fragments ;

- pas de prologue ni d'épilogues ; un prologue et un ou plusieurs épilogues dans d'autres fragments ;

- des épilogues uniquement ; un prologue et éventuellement des épilogues supplémentaires dans d'autres fragments.

Dans le premier cas, seul le prologue doit être décrit. Cela peut être fait sous forme compacte `.pdata` en décrivant le prologue normalement et en spécifiant la *`Ret`* valeur 3 pour indiquer qu’il n’y a pas de épilogue. Dans la `.xdata` forme complète, vous pouvez effectuer cette opération en fournissant les codes de déroulement du prologue à l’index 0 comme d’habitude, et en spécifiant un nombre de épilogue égal à 0.

Le deuxième cas s'apparente tout simplement à une fonction normale. S’il n’existe qu’un seul épilogue dans le fragment et qu’il se trouve à la fin du fragment, un `.pdata` enregistrement compact peut être utilisé. Dans le cas contraire, un `.xdata` enregistrement complet doit être utilisé. Gardez à l'esprit que les décalages spécifiés pour le début de l'épilogue sont fonction du début du fragment, et non du début initial de la fonction.

Les troisième et quatrième cas sont des variantes du premier et du deuxième cas, respectivement, sauf qu’ils ne contiennent pas de prologue. Dans ces situations, du code est censé précéder l'épilogue et est considéré comme faisant partie du corps de la fonction, dont le déroulement procède normalement de l'annulation des effets du prologue. Ces cas doivent ainsi être encodés avec un pseudo-prologue, qui décrit la façon dont le déroulement s'opère à partir du corps, mais qui est considéré comme étant de longueur nulle au moment de déterminer si un déroulement partiel doit être effectué au début du fragment. Ce pseudo-prologue peut aussi être décrit en utilisant les mêmes codes de déroulement que l'épilogue, car on peut supposer qu'ils effectuent des opérations équivalentes.

Dans les troisième et quatrième cas, la présence d’un Pseudo-prologue est spécifiée soit en définissant le *`Flag`* champ de l' `.pdata` enregistrement compact sur 2, soit en affectant la valeur 1 à l’indicateur *F* dans l' `.xdata` en-tête. Dans les deux cas, la recherche d'un déroulement de prologue partiel est ignorée et tous les déroulements non liés aux épilogues sont considérés comme complets.

#### <a name="large-functions"></a>Grandes fonctions

Les fragments peuvent être utilisés pour décrire des fonctions supérieures à la limite de 512 Ko imposée par les champs de bits dans l' `.xdata` en-tête. Pour décrire une fonction très volumineuse, il suffit de la décomposer en fragments inférieurs à 512 Ko. Chaque fragment doit être ajusté afin qu'il ne divise pas un épilogue en plusieurs parties.

Seul le premier fragment de la fonction contient un prologue ; tous les autres fragments sont marqués comme n'ayant pas de prologue. Selon le nombre d'épilogues, chaque fragment peut contenir aucun ou plusieurs épilogues. Ne perdez pas de vue que chaque portée d'épilogue d'un fragment spécifie son décalage de départ par rapport au début du fragment, et non au début de la fonction.

Si un fragment n’a pas de prologue ni de épilogue, il requiert toujours son propre `.pdata` (et éventuellement `.xdata` ) enregistrement pour décrire comment se dérouler à partir du corps de la fonction.

#### <a name="shrink-wrapping"></a>Emballage par rétraction

Un cas spécial plus complexe de fragments de fonction est le retour à la version *réduit*, une technique pour reporter les enregistrements de Registre du début de la fonction à la version ultérieure dans la fonction, afin d’optimiser les cas simples qui ne nécessitent pas d’enregistrement de registres. D'un côté, une région externe alloue l'espace de la pile mais enregistre un ensemble minimal de registres et d'un autre, une région interne enregistre et restaure des registres supplémentaires.

```asm
ShrinkWrappedFunction
    push   {r4, lr}          ; A: save minimal non-volatiles
    sub    sp, sp, #0x100    ; A: allocate all stack space up front
    ...                      ; A:
    add    r0, sp, #0xE4     ; A: prepare to do the inner save
    stm    r0, {r5-r11}      ; A: save remaining non-volatiles
    ...                      ; B:
    add    r0, sp, #0xE4     ; B: prepare to do the inner restore
    ldm    r0, {r5-r11}      ; B: restore remaining non-volatiles
    ...                      ; C:
    pop    {r4, pc}          ; C:
```

Les fonctions emballées par rétractation sont en principe censées préallouer l'espace pour les enregistrements de registre supplémentaires dans le prologue normal et procéder ensuite aux enregistrements de registres à l'aide de `str` ou `stm` à la place de `push`. Cela permet de conserver toutes les manipulations de pointeur de pile dans le prologue d’origine de la fonction.

La fonction emballée par rétraction prise pour exemple doit être divisée en trois régions, qui correspondent aux lettres A, B et C dans les commentaires. La première région A s'étend du début de la fonction jusqu'à la fin des enregistrements non volatifs supplémentaires. Un `.pdata` `.xdata` enregistrement ou doit être construit pour décrire ce fragment comme ayant un prologue et aucun épilogues.

La région B du milieu obtient son propre `.pdata` ou `.xdata` enregistrement qui décrit un fragment qui n’a pas de prologue ni de épilogue. Cependant, des codes de déroulement doivent toujours être présents pour cette région, car elle est considérée comme un corps de fonction. Les codes doivent décrire un prologue composite qui représente à la fois les registres initiaux enregistrés dans le prologue de la région A et les registres supplémentaires enregistrés avant d'entrer dans la région B, comme s'ils étaient générés par une même séquence d'opérations.

Les enregistrements de registres de la région B ne peuvent pas être considérés comme un « prologue interne », car le prologue composite décrit pour la région B doit décrire à la fois le prologue de la région A et les registres supplémentaires enregistrés. S’il était indiqué que le fragment B contenait un prologue, la taille de ce prologue serait aussi induite par les codes de déroulement. Or, il n’existe aucun moyen de décrire le prologue composite qui autorise un mappage un-à-un avec les opcodes qui enregistrent uniquement les registres supplémentaires.

Les enregistrements de registres supplémentaires doivent être considérés comme faisant partie de la région A, car tant qu'ils n'ont pas été menés à bien, le prologue composite ne décrit pas avec précision l'état de la pile.

La dernière région C obtient son propre `.pdata` ou `.xdata` enregistrement, décrivant un fragment qui n’a pas de prologue mais qui a un épilogue.

Une autre approche peut aussi fonctionner si les manipulations de la pile réalisées avant l'entrée dans la région B peuvent être réduites à une seule instruction :

```asm
ShrinkWrappedFunction
    push   {r4, lr}          ; A: save minimal non-volatile registers
    sub    sp, sp, #0xE0     ; A: allocate minimal stack space up front
    ...                      ; A:
    push   {r4-r9}           ; A: save remaining non-volatiles
    ...                      ; B:
    pop    {r4-r9}           ; B: restore remaining non-volatiles
    ...                      ; C:
    pop    {r4, pc}          ; C: restore non-volatile registers
```

Ce qui importe ici, c'est qu'à chaque limite d'instruction, la pile est entièrement cohérente par rapport aux codes de déroulement de la région. Si un déroulement se produit avant le push interne de cet exemple, il est considéré comme faisant partie de la région A et seul le prologue de la région A prologue fait l'objet d'un déroulement. Si le déroulement se produit après le push interne, il est considéré comme faisant partie de la région B, qui n’a pas de prologue, mais qui a des codes de déroulement qui décrivent à la fois le push interne et le prologue d’origine de la région A. la logique similaire contient le point de présence interne.

### <a name="encoding-optimizations"></a>Encodage d'optimisations

En raison de la richesse des codes de déroulement et de la possibilité d’exploiter des formes compactes et étendues de données, il existe de nombreuses opportunités d’optimiser l’encodage pour réduire davantage l’espace. Avec une utilisation intensive de ces techniques, la surcharge nette de description des fonctions et des fragments à l’aide de codes de déroulement peut être réduite.

L'optimisation la plus importante consiste à faire attention à ne pas confondre les limites de prologue/épilogue en vue d'un déroulement avec les limites de prologue/épilogue du point de vue du compilateur. Les limites de déroulement peuvent être réduites et resserrées pour améliorer l'efficacité. Par exemple, un prologue peut contenir du code après la configuration de la pile pour effectuer des vérifications supplémentaires. Mais une fois que toutes les manipulations de pile ont été réalisées, il n'est pas utile d'encoder d'autres opérations et tout ce qui se trouve au-delà peut être supprimé du prologue de déroulement.

La même règle s'applique à la longueur des fonctions. S’il y a des données (par exemple, un pool de littéraux) qui suivent un épilogue dans une fonction, elle ne doit pas être incluse dans le cadre de la longueur de la fonction. En réduisant la fonction à la seule partie du code qui fait partie de la fonction, il est plus probable que le épilogue se trouve à la fin et un `.pdata` enregistrement compact peut être utilisé.

Dans un prologue, une fois que le pointeur de pile est enregistré dans un autre registre, il n’est généralement pas nécessaire d’enregistrer d’autres OpCodes. Pour dérouler la fonction, la première chose à faire est de récupérer le SP à partir du Registre enregistré, et les autres opérations n’ont aucun impact sur le déroulement.

Les épilogues à instruction unique n’ont pas besoin d’être encodés, que ce soit comme étendues ou comme codes de déroulement. Si un déroulement se produit avant l’exécution de cette instruction, il peut être supposé être de l’intérieur du corps de la fonction ; Il suffit d’exécuter les codes de déroulement du prologue. Si le déroulement se produit après l'exécution de l'instruction unique, elle se produit de fait dans une autre région.

Les épilogues à plusieurs instructions n’ont pas besoin d’encoder la première instruction du épilogue, pour la même raison que le point précédent : si le déroulement a lieu avant l’exécution de cette instruction, un déroulement de prologue complet est suffisant. Si le déroulement se produit après cette instruction, seules les opérations suivantes doivent être prises en considération.

La réutilisation du code de déroulement doit être agressive. L'index spécifié par chaque portée d'épilogue pointe vers un point de départ arbitraire dans le tableau des codes de déroulement. Il ne doit pas nécessairement pointer vers le début d'une séquence précédente ; il peut pointer vers le milieu. La meilleure approche consiste à générer la séquence de code souhaitée, puis à rechercher une correspondance exacte d’octets dans le pool de séquences déjà encodé. Utilisez n’importe quelle correspondance parfaite comme point de départ pour la réutilisation.

Une fois les épiloguess à instruction unique ignorés, s’il n’y a pas de épilogues restants, envisagez d’utiliser un `.pdata` format compact ; il devient bien plus probable en l’absence d’un épilogue.

## <a name="examples"></a>Exemples

Dans ces exemples, la base d'image se trouve au niveau de 0x00400000.

### <a name="example-1-leaf-function-no-locals"></a>Exemple 1 : fonction terminale, pas de variables locales

```asm
Prologue:
  004535F8: B430      push        {r4-r5}
Epilogue:
  00453656: BC30      pop         {r4-r5}
  00453658: 4770      bx          lr
```

.pdata (fixe, 2 mots) :

- Mot 0

  - *`Function Start RVA`* = 0x000535F8 (= 0x004535F8-0x00400000)

- Mot 1

  - *`Flag`* = 1, ce qui indique les formats canoniques prologue et épilogue

  - *`Function Length`* = 0x31 (= 0x62/2)

  - *`Ret`* = 1, ce qui indique un retour de branche de 16 bits

  - *`H`* = 0, ce qui indique que les paramètres n’ont pas été hébergés

  - *`R`*= 0 et *`Reg`* = 1, indiquant push/pop de R4-R5

  - *`L`* = 0, ce qui indique l’absence d’enregistrement/restauration LR

  - *`C`* = 0, ce qui indique qu’il n’y a pas de chaînage de frame

  - *`Stack Adjust`* = 0, ce qui indique aucun ajustement de la pile

### <a name="example-2-nested-function-with-local-allocation"></a>Exemple 2 : fonction imbriquée avec allocation locale

```asm
Prologue:
  004533AC: B5F0      push        {r4-r7, lr}
  004533AE: B083      sub         sp, sp, #0xC
Epilogue:
  00453412: B003      add         sp, sp, #0xC
  00453414: BDF0      pop         {r4-r7, pc}
```

.pdata (fixe, 2 mots) :

- Mot 0

  - *`Function Start RVA`* = 0x000533AC (= 0x004533AC-0x00400000)

- Mot 1

  - *`Flag`* = 1, ce qui indique les formats canoniques prologue et épilogue

  - *`Function Length`* = 0x35 (= 0x6A/2)

  - *`Ret`* = 0, ce qui indique un retour de {PC} pop

  - *`H`* = 0, ce qui indique que les paramètres n’ont pas été hébergés

  - *`R`*= 0 et *`Reg`* = 3, ce qui indique un push/pop de R4-R7

  - *`L`* = 1, indiquant que le GD a été enregistré/restauré

  - *`C`* = 0, ce qui indique qu’il n’y a pas de chaînage de frame

  - *`Stack Adjust`* = 3 (= 0x0C/4)

### <a name="example-3-nested-variadic-function"></a>Exemple 3 : fonction variadique imbriquée

```asm
Prologue:
  00453988: B40F      push        {r0-r3}
  0045398A: B570      push        {r4-r6, lr}
Epilogue:
  004539D4: E8BD 4070 pop         {r4-r6}
  004539D8: F85D FB14 ldr         pc, [sp], #0x14
```

.pdata (fixe, 2 mots) :

- Mot 0

  - *`Function Start RVA`* = 0x00053988 (= 0x00453988-0x00400000)

- Mot 1

  - *`Flag`* = 1, ce qui indique les formats canoniques prologue et épilogue

  - *`Function Length`* = 0x2A (= 0x54/2)

  - *`Ret`* = 0, ce qui indique un retour de style pop {PC} (dans ce cas, un `ldr pc,[sp],#0x14` retour)

  - *`H`* = 1, indiquant que les paramètres ont été hébergés

  - *`R`*= 0 et *`Reg`* = 2, ce qui indique un push/pop de R4-R6

  - *`L`* = 1, indiquant que le GD a été enregistré/restauré

  - *`C`* = 0, ce qui indique qu’il n’y a pas de chaînage de frame

  - *`Stack Adjust`* = 0, ce qui indique aucun ajustement de la pile

### <a name="example-4-function-with-multiple-epilogues"></a>Exemple 4 : fonction avec plusieurs épilogues

```asm
Prologue:
  004592F4: E92D 47F0 stmdb       sp!, {r4-r10, lr}
  004592F8: B086      sub         sp, sp, #0x18
Epilogues:
  00459316: B006      add         sp, sp, #0x18
  00459318: E8BD 87F0 ldm         sp!, {r4-r10, pc}
  ...
  0045943E: B006      add         sp, sp, #0x18
  00459440: E8BD 87F0 ldm         sp!, {r4-r10, pc}
  ...
  004595D4: B006      add         sp, sp, #0x18
  004595D6: E8BD 87F0 ldm         sp!, {r4-r10, pc}
  ...
  00459606: B006      add         sp, sp, #0x18
  00459608: E8BD 87F0 ldm         sp!, {r4-r10, pc}
  ...
  00459636: F028 FF0F bl          KeBugCheckEx     ; end of function
```

.pdata (fixe, 2 mots) :

- Mot 0

  - *`Function Start RVA`* = 0x000592F4 (= 0x004592F4-0x00400000)

- Mot 1

  - *`Flag`* = 0, indiquant que l' `.xdata` enregistrement est présent (requis pour plusieurs épilogues)

  - *`.xdata` adresse* -0x00400000

`.xdata` (variable, 6 mots) :

- Mot 0

  - *`Function Length`* = 0x0001A3 (= 0x000346/2)

  - *Vers* = 0, indiquant la première version de`.xdata`

  - *X* = 0, ce qui n’indique aucune donnée d’exception

  - *`E`* = 0, ce qui indique une liste d’étendues de épilogue

  - *F* = 0, indiquant une description complète de la fonction, y compris le prologue

  - *Épilogue Count* = 0x04, qui indique le nombre total de portées épilogue

  - *Mots de code* = 0x01, indiquant un mot de 1 32 bits de codes de déroulement

- Mots 1 à 4, décrivant 4 portées d'épilogue à 4 emplacements. À chaque portée correspond un ensemble commun de codes de déroulement, partagé avec le prologue, au niveau du décalage 0x00, et inconditionnel, spécifiant la condition 0x0E (toujours).

- Codes de déroulement, commençant au Mot 5 : (partagé entre le prologue et l'épilogue)

  - Code de déroulement 0 = 0x06 : SP + = (6 << 2)

  - Code de déroulement 1 = 0xDE : pop {r4-r10, lr}

  - Code de déroulement 2 = 0xFF : fin

### <a name="example-5-function-with-dynamic-stack-and-inner-epilogue"></a>Exemple 5 : fonction avec pile dynamique et épilogue interne

```asm
Prologue:
  00485A20: B40F      push        {r0-r3}
  00485A22: E92D 41F0 stmdb       sp!, {r4-r8, lr}
  00485A26: 466E      mov         r6, sp
  00485A28: 0934      lsrs        r4, r6, #4
  00485A2A: 0124      lsls        r4, r4, #4
  00485A2C: 46A5      mov         sp, r4
  00485A2E: F2AD 2D90 subw        sp, sp, #0x290
Epilogue:
  00485BAC: 46B5      mov         sp, r6
  00485BAE: E8BD 41F0 ldm         sp!, {r4-r8, lr}
  00485BB2: B004      add         sp, sp, #0x10
  00485BB4: 4770      bx          lr
  ...
  00485E2A: F7FF BE7D b           #0x485B28    ; end of function
```

.pdata (fixe, 2 mots) :

- Mot 0

  - *`Function Start RVA`* = 0x00085A20 (= 0x00485A20-0x00400000)

- Mot 1

  - *`Flag`* = 0, ce qui indique que l' `.xdata` enregistrement est présent (nécessaire pour plusieurs épilogues)

  - *`.xdata` adresse* -0x00400000

`.xdata` (variable, 3 mots) :

- Mot 0

  - *`Function Length`* = 0x0001A3 (= 0x000346/2)

  - *Vers* = 0, indiquant la première version de`.xdata`

  - *X* = 0, ce qui n’indique aucune donnée d’exception

  - *`E`* = 0, ce qui indique une liste d’étendues de épilogue

  - *F* = 0, indiquant une description complète de la fonction, y compris le prologue

  - *Épilogue Count* = 0x001, indiquant la portée totale du épilogue

  - *Mots de code* = 0x01, indiquant un mot de 1 32 bits de codes de déroulement

- Mot 1 : portée d'épilogue au niveau du décalage 0xC6 (= 0x18C/2), index du code de déroulement de départ à 0x00, avec une condition de 0x0E (toujours)

- Codes de déroulement, commençant au Mot 2 : (partagé entre le prologue et l'épilogue)

  - Code de déroulement 0 = 0xC6 : sp = r6

  - Code de déroulement 1 = 0xDC : pop {r4-r8, lr}

  - Code de déroulement 2 = 0x04 : SP + = (4 << 2)

  - Code de déroulement 3 = 0xFD : fin, compte comme une instruction de 16 bits pour l'épilogue

### <a name="example-6-function-with-exception-handler"></a>Exemple 6 : fonction avec un gestionnaire d'exceptions

```asm
Prologue:
  00488C1C: 0059 A7ED dc.w  0x0059A7ED
  00488C20: 005A 8ED0 dc.w  0x005A8ED0
FunctionStart:
  00488C24: B590      push        {r4, r7, lr}
  00488C26: B085      sub         sp, sp, #0x14
  00488C28: 466F      mov         r7, sp
Epilogue:
  00488C6C: 46BD      mov         sp, r7
  00488C6E: B005      add         sp, sp, #0x14
  00488C70: BD90      pop         {r4, r7, pc}
```

.pdata (fixe, 2 mots) :

- Mot 0

  - *`Function Start RVA`* = 0x00088C24 (= 0x00488C24-0x00400000)

- Mot 1

  - *`Flag`* = 0, ce qui indique que l' `.xdata` enregistrement est présent (nécessaire pour plusieurs épilogues)

  - *`.xdata` adresse* -0x00400000

`.xdata` (variable, 5 mots) :

- Mot 0

  - *`Function Length`* = 0x000027 (= 0x00004E/2)

  - *Vers* = 0, indiquant la première version de`.xdata`

  - *X* = 1, indiquant les données d’exception présentes

  - *`E`* = 1, ce qui indique un seul épilogue

  - *F* = 0, indiquant une description complète de la fonction, y compris le prologue

  - *Épilogue Count* = 0x00, qui indique que les codes de déroulement épilogue démarrent au décalage 0x00

  - *Code Words* = 0x02, indiquant des mots de 2 32 bits de codes de déroulement

- Codes de déroulement, commençant au Mot 1 :

  - Code de déroulement 0 = 0xC7 : sp = r7

  - Code de déroulement 1 = 0x05 : SP + = (5 << 2)

  - Code de déroulement 2 = 0xED/0x90 : pop {r4, r7, lr}

  - Code de déroulement 4 = 0xFF : fin

- Le mot 3 spécifie un gestionnaire d’exceptions = 0x0019A7ED (= 0x0059A7ED-0x00400000)

- Les mots 4 et suivants sont des données d'exception inline

### <a name="example-7-funclet"></a>Exemple 7 : Funclet

```asm
Function:
  00488C72: B500      push        {lr}
  00488C74: B081      sub         sp, sp, #4
  00488C76: 3F20      subs        r7, #0x20
  00488C78: F117 0308 adds        r3, r7, #8
  00488C7C: 1D3A      adds        r2, r7, #4
  00488C7E: 1C39      adds        r1, r7, #0
  00488C80: F7FF FFAC bl          target
  00488C84: B001      add         sp, sp, #4
  00488C86: BD00      pop         {pc}
```

.pdata (fixe, 2 mots) :

- Mot 0

  - *`Function Start RVA`* = 0x00088C72 (= 0x00488C72-0x00400000)

- Mot 1

  - *`Flag`* = 1, ce qui indique les formats canoniques prologue et épilogue

  - *`Function Length`* = 0x0B (= 0x16/2)

  - *`Ret`* = 0, ce qui indique un retour de {PC} pop

  - *`H`* = 0, ce qui indique que les paramètres n’ont pas été hébergés

  - *`R`*= 0 et *`Reg`* = 7, ce qui indique qu’aucun registre n’a été enregistré/restauré

  - *`L`* = 1, indiquant que le GD a été enregistré/restauré

  - *`C`* = 0, ce qui indique qu’il n’y a pas de chaînage de frame

  - *`Stack Adjust`* = 1, ce qui indique un ajustement de pile de 1 × 4 octets

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble des conventions ABI ARM](overview-of-arm-abi-conventions.md)<br/>
[Problèmes courants de migration ARM Visual C++](common-visual-cpp-arm-migration-issues.md)
