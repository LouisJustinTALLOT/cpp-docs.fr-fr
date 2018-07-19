---
title: La gestion des exceptions ARM | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fe0e615f-c033-4ad5-97f4-ff96af45b201
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef0756875a799aacaf7308c406d98cbbf3a9a2a2
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2018
ms.locfileid: "39027964"
---
# <a name="arm-exception-handling"></a>Gestion des exceptions ARM

Windows on ARM utilise le même mécanisme de gestion des exceptions structurées pour les exceptions asynchrones générées par le matériel et les exceptions synchrones générées par les logiciels. Les gestionnaires d'exceptions propres aux langages s'appuient sur la gestion des exceptions structurées Windows en utilisant des fonctions d'assistance de langage. Ce document décrit la gestion des exceptions dans Windows sur ARM et les programmes d’assistance de langage utilisés par le code généré par l’assembleur Microsoft ARM et le compilateur Visual C++.

## <a name="arm-exception-handling"></a>Gestion des exceptions ARM

Utilise Windows sur ARM *codes de déroulement* pour contrôler le déroulement de pile pendant [structurée des exceptions](http://msdn.microsoft.com/library/windows/desktop/ms680657) (SEH). Les codes de déroulement consistent en une séquence d’octets stockés dans la section .xdata de l’image exécutable. Ils décrivent l'opération du code de prologue et d'épilogue de la fonction de manière abstraite, ce qui permet d'annuler les effets du prologue d'une fonction en préparation du déroulement dans le frame de pile de l'appelant.

L'interface EABI (Embedded Application Binary Interface) ARM spécifie un modèle de déroulement d'exception qui utilise les codes de déroulement, mais cela n'est pas suffisant pour le déroulement SEH dans Windows, qui doit gérer les cas asynchrones où le processeur se situe au milieu du prologue ou de l'épilogue d'une fonction. De même, Windows sépare le contrôle du déroulement en déroulement au niveau de la fonction et en déroulement de portée propre au langage, qui est unifié dans l'interface EABI ARM. Pour ces raisons, Windows on ARM spécifie plus de détails pour les données et la procédure de déroulement.

### <a name="assumptions"></a>Assumptions (Hypothèses)

Les images exécutables pour Windows on ARM utilisent le format PE (Portable Executable). Pour plus d’informations, consultez [spécification Microsoft PE et COFF](http://go.microsoft.com/fwlink/p/?linkid=84140). Les informations de gestion des exceptions sont stockées dans les sections .pdata et .xdata de l'image.

Le mécanisme de gestion des exceptions établit certaines hypothèses concernant le code qui suit l'interface ABI pour Windows on ARM :

- Quand une exception se produit dans le corps d'une fonction, peu importe si les opérations du prologue sont annulées ou si les opérations de l'épilogue sont effectuées à l'avance. Les deux doivent produire des résultats identiques.

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

### <a name="pdata-records"></a>Enregistrements .pdata

Les enregistrements .pdata d'une image au format PE consistent en un tableau ordonné d'éléments de longueur fixe qui décrivent chaque fonction de manipulation de pile. Les fonctions terminales, qui sont des fonctions qui n'appellent pas d'autres fonctions, n'ont pas besoin d'enregistrements .pdata quand elles ne manipulent pas la pile. (Autrement dit, elles n'ont besoin ni de stockage local ni d'enregistrer ou restaurer des registres non volatils.) Les enregistrements liés à ces fonctions peuvent être omis dans la section .pdata pour économiser de l'espace. Une opération de déroulement de l'une de ces fonctions peut simplement copier l'adresse de retour du registre de liaison (ou LR, Link Register) dans le compteur de programme (ou PC, Program Counter) à déplacer vers l'appelant.

Chaque enregistrement .pdata pour ARM a une longueur de 8 octets. Dans le format général d'un enregistrement, l'adresse virtuelle relative (ou RVA, Relative Virtual Address) du début de la fonction est placée dans le premier mot de 32 bits, qui est suivi d'un deuxième mot contenant soit un pointeur vers un bloc .xdata de longueur variable, soit un mot compressé qui décrit une séquence de déroulement de fonction canonique, comme dans le tableau suivant :

|Décalage de mot|Bits|Objectif|
|-----------------|----------|-------------|
|0|0-31|*Fonction RVA Démarrer* est l’adresse RVA 32 bits du début de la fonction. Si la fonction contient du code thumb, le bit inférieur de cette adresse doit être défini.|
|1|0-1|*Indicateur* est un champ de 2 bits qui indique comment interpréter les 30 bits restants du deuxième mot .pdata. Si *indicateur* est égal à 0, puis les bits restants forment un *Exception informations RVA* (avec les deux bits inférieurs ayant implicitement la valeur 0). Si *indicateur* est différente de zéro, puis les bits restants forment un *données de déroulement compressées* structure.|
|1|2-31|*Informations sur les exceptions RVA* ou *emballés données de déroulement*.<br /><br /> *Exception informations RVA* est l’adresse de la structure d’informations d’exceptions de longueur variable stockée dans la section .xdata. Ces données doivent être alignées sur 4 octets.<br /><br /> *Compressé des données de déroulement* est une description compressée des opérations nécessaires au déroulement à partir d’une fonction, en supposant que la forme canonique. Dans ce cas, aucun enregistrement .xdata n'est nécessaire.|

### <a name="packed-unwind-data"></a>Données de déroulement compressées

Pour les fonctions dont les prologues et les épilogues suivent la forme canonique décrite ci-dessous, il est possible d'utiliser des données de déroulement compressées. Cela permet de se passer d'un enregistrement .xdata tout en réduisant considérablement l'espace nécessaire pour fournir les données de déroulement. Les prologues et épilogues canoniques visent à répondre aux besoins courants d'une fonction simple qui ne nécessite pas de gestionnaire d'exceptions et qui effectue ses opérations de configuration et de démontage dans un ordre normal.

Ce tableau présente le format d'un enregistrement .pdata qui contient des données de déroulement compressées :

|Décalage de mot|Bits|Objectif|
|-----------------|----------|-------------|
|0|0-31|*Fonction RVA Démarrer* est l’adresse RVA 32 bits du début de la fonction. Si la fonction contient du code thumb, le bit inférieur de cette adresse doit être défini.|
|1|0-1|*Indicateur* est un champ de 2 bits qui a ces significations :<br /><br /> -00 = compressé déroulement des données non utilisées ; bits restants pointent vers un enregistrement .xdata.<br />-01 = compressé données de déroulement.<br />-10 = compressé données où la fonction est censée pour avoir pas de prologue de déroulement. Ceci est utile pour décrire les fragments de fonction discontinus par rapport au début de la fonction.<br />-11 = réservée.|
|1|2-12|*Longueur de la fonction* est un champ de 11 bits qui fournit la longueur de la fonction entière en octets divisée par 2. Si la longueur de la fonction est supérieure à 4 K octets, un enregistrement .xdata complet doit être utilisé à la place.|
|1|13-14|*RET* est un champ de 2 bits qui indique comment la fonction retourne :<br /><br /> -00 = retour via pop {pc} (le *L* bit indicateur doit être définie sur 1 dans ce cas).<br />-01 = retour via une branche de 16 bits.<br />-10 = retour via une branche de 32 bits.<br />-11 = absence d’épilogue du tout. Ceci est utile pour décrire un fragment de fonction discontinu qui peut ne contenir qu'un prologue, mais dont l'épilogue se trouve ailleurs.|
|1|15|*H* est un indicateur de 1 bit qui indique si la fonction « héberge » le paramètre entier inscrit (r0-r3) en les envoyant au début de la fonction et libère les 16 octets de pile avant de retourner. (0 = n'héberge pas les registres, 1 = héberge les registres.)|
|1|16-18|*Reg* est un champ de 3 bits qui indique l’index du dernier enregistré non volatile register. Si le *R* bit est 0, uniquement des registres d’entiers sont enregistrés et sont supposés pour être dans la plage r4-RN, où N est égal à 4 + *Reg*. Si le *R* bit est 1, puis les registres en virgule flottante uniquement sont enregistrées et sont supposés pour être dans la plage d8-DN, où N est égal à 8 + *Reg*. La combinaison spéciale de *R* = 1 et *Reg* = 7 indique qu’aucun registre n’est enregistré.|
|1|19|*R* est un indicateur de 1 bit qui indique si les registres non volatils enregistrés sont des registres d’entiers (0) ou registres en virgule flottante (1). Si *R* est défini sur 1 et le *Reg* champ est défini sur 7, les registres non volatils ont été envoyés.|
|1|20|*L* est un indicateur de 1 bit qui indique si la fonction enregistre/restaure le Registre LR, ainsi que d’autres registres indiqués par le *Reg* champ. (0 = n'enregistre/ne restaure pas, 1 = enregistre/restaure.)|
|1|21|*C* est un indicateur de 1 bit qui indique si la fonction inclut des instructions supplémentaires pour configurer une chaîne de frames pour l’exploration de pile rapide (1) ou non (0). Si ce bit est défini, le registre r11 est ajouté implicitement à la liste des registres non volatils d'entiers enregistrés. (Voir les restrictions ci-dessous si le *C* indicateur est utilisé.)|
|1|22-31|*Ajuster la pile* est un champ de 10 bits qui indique le nombre d’octets de pile qui sont alloués pour cette fonction, divisée par 4. Cependant, seules les valeurs comprises entre 0x000 et 0x3F3 peuvent être directement encodées. Les fonctions qui allouent plus de 4 044 octets de pile doivent utiliser un enregistrement .xdata complet. Si le *ajuster Stack* champ est égal à 0x3F4 ou plus, alors les 4 bits inférieurs ont une signification particulière :<br /><br /> -Bits 0-1 indiquent le nombre de mots d’ajustement de pile (1-4) moins 1.<br />-Bit 2 est défini sur 1 si le prologue a combiné cet ajustement dans son opération push.<br />-Bit 3 est défini sur 1 si l’épilogue a combiné cet ajustement dans son opération pop.|

Du fait des redondances possibles dans les encodages précédents, les restrictions suivantes s'appliquent :

- Si le *C* indicateur est défini sur 1 :

   - Le *L* indicateur doit également être défini sur 1, étant donné que le chaînage de frames requis r11 et LR.

   - R11 ne doit pas être inclus dans le jeu de registres décrit par *Reg*. Autrement dit, si les registres r4 à r11 est envoyées, *Reg* doit décrire uniquement r4-r10, car le *C* cet indicateur implique r11.

- Si le *Ret* champ est défini sur 0, le *L* l’indicateur doit être défini sur 1.

La violation de ces restrictions donne lieu à une séquence non prise en charge.

Pour les besoins de l’explication ci-dessous, deux pseudo-indicateurs sont dérivés de *ajuster Stack*:

- *PF* ou « prologue folding » indique que *ajuster Stack* est égal à 0x3F4 ou 2 et que le bit est défini.

- *EF* ou « epilogue folding » indique que *ajuster Stack* est égal à 0x3F4 ou 3 et que le bit est défini.

Les prologues des fonctions canoniques peuvent avoir jusqu'à 5 instructions (à noter que les instructions 3a et 3b s'excluent mutuellement) :

|Instruction|Un opcode est considéré être présent si :|Taille|Opcode|Codes de déroulement|
|-----------------|-----------------------------------|----------|------------|------------------|
|1|*H*== 1|16|`push {r0-r3}`|04|
|2|*C*== 1 ou *L*== 1 ou *R*== 0 ou PF == 1|16/32|`push {registers}`|80-BF/D0-DF/EC-ED|
|3a|*C*== 1 et (*L*== 0 et *R*== 1 et PF == 0)|16|`mov r11,sp`|C0-CF/FB|
|3b|*C*== 1 et (*L*== 1 ou *R*== 0 ou PF == 1)|32|`add r11,sp,#xx`|FC|
|4|*R*== 1 et *Reg* ! = 7|32|`vpush {d8-dE}`|E0-E7|
|5|*Pile ajuster* ! = 0 et PF == 0|16/32|`sub sp,sp,#xx`|00-7F/E8-EB|

Instruction 1 est toujours présente si le *H* bit est défini sur 1.

Pour configurer le chaînage de frames, instruction 3 a ou 3 b est présent si la *C* bit est défini. Il s'agit d'un `mov` de 16 bits si aucun autre registre que r11 et LR ne fait l'objet d'un push ; sinon, il s'agit d'un `add` de 32 bits.

Si un ajustement non plié est spécifié, l'instruction 5 est l'ajustement de pile explicite.

Les instructions 2 et 4 sont définies selon qu'un push est nécessaire ou pas. Le tableau suivant résume les registres qui sont enregistrés en fonction de la *C*, *L*, *R*, et *PF* champs. Dans tous les cas, *N* est égal à *Reg* + 4, *E* est égal à *Reg* + 8, et *S* est égal à (~*Pile ajuster*) & 3.

|C|L|R|PF|Registres d'entiers faisant l'objet d'un push|Registres VFP faisant l'objet d'un push|
|-------|-------|-------|--------|------------------------------|--------------------------|
|0|0|0|0|R4-r*N*|none|
|0|0|0|1|r*S*- r*N*|none|
|0|0|1|0|none|d-D8*E*|
|0|0|1|1|r*S*-r3|d-D8*E*|
|0|1|0|0|R4-r*N*, LR|none|
|0|1|0|1|r*S*- r*N*, LR|none|
|0|1|1|0|LR|d-D8*E*|
|0|1|1|1|r*S*-r3, LR|d-D8*E*|
|1|0|0|0|R4-r*N*, r11|none|
|1|0|0|1|r*S*- r*N*, r11|none|
|1|0|1|0|r11|d-D8*E*|
|1|0|1|1|r*S*-r3, r11|d-D8*E*|
|1|1|0|0|R4-r*N*, r11, LR|none|
|1|1|0|1|r*S*- r*N*, r11, LR|none|
|1|1|1|0|r11, LR|d-D8*E*|
|1|1|1|1|r*S*-r3, r11, LR|d-D8*E*|

Les épilogues des fonctions canoniques suivent une forme analogue, mais en sens inverse et avec quelques options supplémentaires. L'épilogue peut compter jusqu'à 5 instructions et sa forme est strictement dictée par celle du prologue.

|Instruction|Un opcode est considéré être présent si :|Taille|Opcode|
|-----------------|-----------------------------------|----------|------------|
|6|*Pile ajuster*! = 0 et *EF*== 0|16/32|`add   sp,sp,#xx`|
|7|*R*== 1 et *Reg*! = 7|32|`vpop  {d8-dE}`|
|8|*C*== 1 ou (*L*== 1 et *H*== 0) ou *R*== 0 ou *EF*== 1|16/32|`pop   {registers}`|
|9a|*H*== 1 et *L*== 0|16|`add   sp,sp,#0x10`|
|9b|*H*== 1 et *L*== 1|32|`ldr   pc,[sp],#0x14`|
|10a|*RET*== 1|16|`bx    reg`|
|10b|*RET*== 2|32|`b     address`|

L’instruction 6 est l’ajustement de pile explicite si un ajustement non plié est spécifié. Étant donné que *PF* est indépendante de *EF*, il est possible d’avoir une instruction 5 présente sans l’instruction 6, ou vice versa.

Instructions 7 et 8 utilisent la même logique que le prologue pour déterminer quels registres sont restaurés à partir de la pile, mais à ces deux différences : tout d’abord, *EF* est utilisé à la place de *PF*; en second lieu, si *Ret*  = 0, LR est remplacé par PC dans la liste des registres et l’épilogue se termine immédiatement.

Si *H* est défini, l’instruction 9 a ou 9 b est présente. Instruction 9 a est utilisé lorsque *L* est 0, pour indiquer que le Registre LR n’est pas sur la pile. Dans ce cas, la pile est ajustée manuellement et *Ret* doit être 1 ou 2 pour spécifier un retour explicite. Instruction 9 b est utilisée lorsque *L* est 1, pour indiquer une fin prématurée de l’épilogue et à retourner et ajuster la pile en même temps.

Si l’épilogue non déjà terminée, puis l’instruction 10 a ou 10 b est présente, pour indiquer une branche de 16 bits ou 32 bits, selon la valeur de *Ret*.

### <a name="xdata-records"></a>Enregistrements .xdata

Quand le format de déroulement compressé ne suffit pas à décrire le déroulement d'une fonction, un enregistrement .xdata de longueur variable doit être créé. L'adresse de cet enregistrement est stockée dans le deuxième mot de l'enregistrement .pdata. Le format de l'enregistrement .xdata est un ensemble de mots compressé de longueur variable qui compte quatre sections :

1. Un en-tête de 1 ou 2 mots qui décrit la taille globale de la structure .xdata et fournit des données de fonction clés. Le deuxième mot n’est présent que si le *épilogue nombre* et *Code mots* champs sont toutes deux définies sur 0. Les champs sont décrits en détail dans ce tableau :

   |Mot|Bits|Objectif|
    |----------|----------|-------------|
    |0|0-17|*Longueur de la fonction* est un champ de 18 bits qui indique la longueur totale de la fonction en octets divisée par 2. Si une fonction dépasse 512 Ko, plusieurs enregistrements .pdata et .xdata doivent être utilisés pour décrire la fonction. Pour plus de détails, consultez la section Grandes fonctions dans ce document.|
    |0|18-19|*Vers* est un champ de 2 bits qui décrit la version de l’enregistrement xdata restant. Seule la version 0 est actuellement définie ; les valeurs 1 à 3 sont réservées.|
    |0|20|*X* est un champ de 1 bit qui indique la présence (1) ou non (0) des données d’exception.|
    |0|21|*E* est un champ de 1 bit qui indique que les informations qui décrivent un épilogue unique sont compressées dans l’en-tête (1) au lieu de demander l’étendue supplémentaire mots ultérieures (0).|
    |0|22|*F* est un champ de 1 bit qui indique que cet enregistrement décrit un fragment de fonction (1) ou une fonction complète (0). Un fragment implique l'absence de prologue et que tout le traitement des prologues doit être ignoré.|
    |0|23-27|*Nombre d’épilogue* est un champ de 5 bits qui a deux significations, selon l’état de la *E* bits :<br /><br /> -If *E* est 0, ce champ indique le nombre total d’étendues d’exception décrites dans la section 3. Si plus de 31 portées existent dans la fonction, puis ce champ et le *Code mots* champ doive être toutes deux défini sur 0 pour indiquer qu’un mot d’extension est nécessaire.<br />-If *E* est 1, ce champ spécifie l’index du premier code de déroulement qui décrit l’épilogue unique.|
    |0|28-31|*Les mots de code* est un champ de 4 bits qui spécifie le nombre de mots de 32 bits nécessaires pour contenir tous les codes de déroulement à la section 4. Si plus de 15 mots sont nécessaires pour plus de 63 octets de code de déroulement, ce champ et le *épilogue nombre* champ doive être toutes deux défini sur 0 pour indiquer qu’un mot d’extension est nécessaire.|
    |1|0-15|*Étendue épilogue nombre* est un champ de 16 bits qui fournit davantage d’espace pour l’encodage d’un nombre exceptionnellement élevé d’épilogues. Le mot d’extension qui contient ce champ n’est présent que si le *épilogue nombre* et *Code mots* champs dans le premier mot d’en-tête sont toutes deux définies sur 0.|
    |1|16-23|*Étendue des mots de Code* est un champ de 8 bits qui fournit davantage d’espace pour l’encodage d’un nombre exceptionnellement élevé de mots de code de déroulement. Le mot d’extension qui contient ce champ n’est présent que si le *épilogue nombre* et *Code mots* champs dans le premier mot d’en-tête sont toutes deux définies sur 0.|
    |1|24-31|Réservée|

2. Une fois les données d’exception (si le *E* bit dans l’en-tête a été défini sur 0) est une liste d’informations sur les portées d’épilogue, qui sont compressées dans un mot et stockées par ordre croissant de décalage de départ. Chaque portée contient ces champs :

   |Bits|Objectif|
    |----------|-------------|
    |0-17|*Décalage de début d’épilogue* est un champ de 18 bits qui décrit le décalage de l’épilogue, en octets divisée par 2, par rapport au début de la fonction.|
    |18-19|*Res* est un champ de 2 bits réservé pour l’expansion future. Il doit avoir la valeur 0.|
    |20-23|*Condition* est un champ de 4 bits qui dicte la condition sous laquelle l’épilogue est exécuté. Pour les épilogues inconditionnels, il doit avoir la valeur 0xE, ce qui indique « toujours ». (Un épilogue doit être entièrement conditionnel ou entièrement inconditionnel, et en mode Thumb-2, l'épilogue commence par la première instruction située après l'opcode IT.)|
    |24-31|*Index de début d’épilogue* est un champ de 8 bits qui indique l’index d’octet du premier code de déroulement qui décrit cet épilogue.|

3. Après la liste des portées d'épilogue figure un tableau d'octets qui contient les codes de déroulement, qui sont décrits en détail dans la section Code de déroulement de cet article. Ce tableau est rempli à la fin jusqu'à la limite du mot complet le plus proche. Les octets sont stockés dans un ordre Little-Endian, ce qui permet de les récupérer directement en mode Little-Endian.

4. Si le *X* champ dans l’en-tête est 1, les octets de code de déroulement sont suivis par les informations de gestionnaire d’exception. Il s’agit d’un *RVA de gestionnaire d’Exception* qui contient l’adresse du Gestionnaire d’exceptions, immédiatement suivi de la quantité de (de longueur variable) de données requises par le Gestionnaire d’exceptions.

L’enregistrement .xdata est conçu pour permettre la récupération des 8 premiers octets et le calcul de la taille complète de l’enregistrement, à l’exclusion de la longueur des données d’exception de taille variable qui suivent. Cet extrait de code permet de calculer la taille de l'enregistrement :

```cpp
ULONG ComputeXdataSize(PULONG *Xdata)
{
    ULONG EpilogueScopes;
    ULONG Size;
    ULONG UnwindWords;

    if ((Xdata[0] >> 23) != 0) {
        Size = 4;
        EpilogueScopes = (Xdata[0] >> 23) & 0x1f;
        UnwindWords = (Xdata[0] >> 28) & 0x0f;
    } else {
        Size = 8;
        EpilogueScopes = Xdata[1] & 0xffff;
        UnwindWords = (Xdata[1] >> 16) & 0xff;
    }

    if (!(Xdata[0] & (1 << 21))) {
        Size += 4 * EpilogueScopes;
    }
    Size += 4 * UnwindWords;
    if (Xdata[0] & (1 << 20)) {
        Size += 4;
    }
    return Size;
}
```

Même si le prologue et chaque épilogue ont un index dans les codes de déroulement, la table est partagée entre eux. Il n'est pas rare qu'ils puissent tous partager les mêmes codes de déroulement. Nous recommandons aux rédacteurs de compilateur de prévoir une optimisation pour ce cas de figure, car la taille maximale d'index est de 255, ce qui limite le nombre total de codes de déroulement possibles pour une fonction déterminée.

### <a name="unwind-codes"></a>Codes de déroulement

Le tableau de codes de déroulement est un pool de séquences d'instructions qui indiquent exactement comment annuler les effets du prologue, dans l'ordre où les opérations doivent être annulées. Les codes de déroulement correspondent à un mini-ensemble d'instructions, encodé sous la forme d'une chaîne d'octets. Une fois l'exécution terminée, l'adresse de retour vers la fonction appelante se trouve dans le registre LR, et tous les registres non volatils sont restaurés avec les valeurs qui étaient les leurs au moment où la fonction a été appelée.

S'il était garanti que les exceptions ne se produisaient que dans le corps d'une fonction et jamais dans un prologue ou un épilogue, une seule séquence de déroulement serait nécessaire. Cependant, le modèle de déroulement Windows impose de pouvoir effectuer un déroulement à partir d'un prologue ou d'un épilogue partiellement exécuté. Pour satisfaire cette exigence, les codes de déroulement ont été soigneusement conçus pour bénéficier d'un mappage un-à-un non équivoque à chaque opcode approprié dans le prologue et l'épilogue. Cela a plusieurs conséquences :

- Il est possible de calculer la longueur du prologue et de l'épilogue en comptant le nombre de codes de déroulement. Cela est possible même avec des instructions Thumb-2 de longueur variable, car il existe des mappages distincts pour les opcodes de 16 et 32 bits.

- En comptant le nombre d'instructions après le début d'une portée d'épilogue, il est possible d'ignorer le nombre équivalent de codes de déroulement et d'exécuter le reste d'une séquence pour terminer le déroulement partiellement exécuté par l'épilogue.

- En comptant le nombre d'instructions avant la fin du prologue, il est possible d'ignorer le nombre équivalent de codes de déroulement et d'exécuter le reste d'une séquence pour annuler uniquement les parties du prologue qui ont mené à bien l'exécution.

Le tableau suivant présente le mappage entre les codes de déroulement et les opcodes. Les codes les plus courants ne font qu'un octet, alors que les moins courants nécessitent deux, trois, voire quatre octets. Chaque code est stocké de l'octet le plus significatif à l'octet le moins significatif. La structure des codes de déroulement est différente de l'encodage décrit dans l'interface EABI ARM, car ces codes de déroulement sont conçus pour bénéficier d'un mappage un-à-un aux opcodes dans le prologue et l'épilogue afin de permettre le déroulement des prologues et épilogues partiellement exécutés.

|Octet 1|Octet 2|Octet 3|Octet 4|Taille d'opcode|Explication|
|------------|------------|------------|------------|------------|-----------------|
|00-7F||||16|`add   sp,sp,#X`<br /><br /> où X correspond à (Code & 0x7F) * 4|
|80-BF|00-FF|||32|`pop   {r0-r12, lr}`<br /><br /> où le registre LR fait l'objet d'un pop si Code & 0x2000 et r0-r12 font l'objet d'un pop si le bit correspondant est défini dans Code & 0x1FFF|
|C0-CF||||16|`mov   sp,rX`<br /><br /> où X correspond à Code & 0x0F|
|D0-D7||||16|`pop   {r4-rX,lr}`<br /><br /> où X correspond à (Code & 0x03) + 4 et LR fait l'objet d'un pop si Code & 0x04|
|D8-DF||||32|`pop   {r4-rX,lr}`<br /><br /> où X correspond à (Code & 0x03) + 8 et LR fait l'objet d'un pop si Code & 0x04|
|E0-E7||||32|`vpop  {d8-dX}`<br /><br /> où X correspond à (Code & 0x07) + 8|
|E8-EB|00-FF|||32|`addw  sp,sp,#X`<br /><br /> où X correspond à (Code & 0x03FF) * 4|
|EC-ED|00-FF|||16|`pop   {r0-r7,lr}`<br /><br /> où le registre LR fait l'objet d'un pop si Code & 0x0100 et r0-r7 font l'objet d'un pop si le bit correspondant est défini dans Code & 0x00FF|
|EE|00-0F|||16|Spécifique à Microsoft|
|EE|10-FF|||16|Disponible|
|EF|00-0F|||32|`ldr   lr,[sp],#X`<br /><br /> où X correspond à (Code & 0x000F) * 4|
|EF|10-FF|||32|Disponible|
|F0-F4||||-|Disponible|
|F5|00-FF|||32|`vpop  {dS-dE}`<br /><br /> où S correspond à (Code & 0x00F0) >> 4 et E à Code & 0x000F|
|F6|00-FF|||32|`vpop  {dS-dE}`<br /><br /> où S correspond à ((Code & 0x00F0) >> 4) + 16 et E à (Code & 0x000F) + 16|
|F7|00-FF|00-FF||16|`add   sp,sp,#X`<br /><br /> où X correspond à (Code & 0x00FFFF) * 4|
|F8|00-FF|00-FF|00-FF|16|`add   sp,sp,#X`<br /><br /> où X correspond à (Code & 0x00FFFFFF) * 4|
|F9|00-FF|00-FF||32|`add   sp,sp,#X`<br /><br /> où X correspond à (Code & 0x00FFFF) * 4|
|FA|00-FF|00-FF|00-FF|32|`add   sp,sp,#X`<br /><br /> où X correspond à (Code & 0x00FFFFFF) * 4|
|FB||||16|nop (16 bits)|
|FC||||32|nop (32 bits)|
|FD||||16|fin + nop de 16 bits dans l'épilogue|
|FE||||32|fin + nop de 32 bits dans l'épilogue|
|FF||||-|end|

Cela montre la plage de valeurs hexadécimales pour chaque octet dans un code de déroulement *Code*, ainsi que la taille d’opcode *Opsize* et l’interprétation de l’instruction d’origine correspondant. Les cellules vides indiquent des codes de déroulement plus courts. Dans les instructions qui contiennent des valeurs élevées couvrant plusieurs octets, les bits les plus significatifs sont stockés en premier. Le *Opsize* champ indique la taille d’opcode implicite associée à chaque opération Thumb-2. Les entrées en double apparentes figurant dans le tableau avec des encodages différents servent à faire la distinction entre les différentes tailles d’opcode.

Les codes de déroulement sont conçus de telle sorte que le premier octet du code indique à la fois la taille totale en octets du code et la taille de l'opcode correspondant dans le flux d'instructions. Pour calculer la taille du prologue ou de l'épilogue, parcourez les codes de déroulement du début jusqu'à la fin de la séquence, puis utilisez une table de correspondance ou une méthode similaire pour déterminer la longueur de l'opcode correspondant.

Les codes de déroulement 0xFD et 0xFE sont équivalents au code de fin normal 0xFF, mais prennent en compte un opcode nop supplémentaire dans le cas de l'épilogue, de 16 ou 32 bits. Pour les prologues, les codes 0xFD, 0xFE et 0xFF sont tout à fait équivalents. Cela prend en compte les fins d'épilogue courantes `bx lr` ou `b <tailcall-target>`, qui n'ont pas d'instruction de prologue équivalente. Cela augmente les probabilités de partage des séquences de déroulement entre le prologue et les épilogues.

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

En regard de chaque opcode figure le code déroulement approprié qui décrit l'opération. La séquence de codes de déroulement du prologue est une image miroir des codes de déroulement de l'épilogue, l'instruction finale en moins. S'agissant d'un cas fréquent, cela explique que les codes de déroulement du prologue sont toujours censés être stockés dans l'ordre inverse de l'ordre d'exécution du prologue. Cela nous donne un ensemble commun de codes de déroulement :

```asm
0xc7, 0xdd, 0x04, 0xfd
```

Le code 0xFD est un code spécial pour la fin de la séquence qui signifie que l'épilogue est plus long que le prologue d'une instruction de 16 bits. Cela permet un plus grand partage de codes de déroulement.

Dans l'exemple, si une exception se produit pendant l'exécution du corps de la fonction entre le prologue et l'épilogue, le déroulement commence par le cas de l'épilogue au décalage 0 dans le code de l'épilogue. Cela correspond au décalage 0x140 dans l'exemple. Le dérouleur exécute la séquence de déroulement complète, car aucun nettoyage n'a été fait. En revanche, si l'exception se produit au niveau de la première instruction suivant le début du code de l'épilogue, le dérouleur peut procéder au déroulement en ignorant le premier code de déroulement. Étant donné un mappage entre les opcodes et codes de déroulement, si le déroulement démarre à partir de l’instruction *n* dans l’épilogue, le dérouleur doit ignorer la première *n* codes de déroulement.

La logique qui prévaut dans le cas du prologue est identique mais inversée. Si le déroulement se produit à partir du décalage 0 dans le prologue, il n'y a rien à exécuter. Si le déroulement démarre à la première instruction, la séquence de déroulement doit commencer au premier code de déroulement en partant de la fin, car les codes de déroulement du prologue sont stockés dans l'ordre inverse. En règle générale, si le déroulement démarre à partir de l’instruction *n* dans le prologue, le déroulement doit commencer à s’exécuter à *n* codes à partir de la fin de la liste des codes de déroulement.

Les codes de déroulement de prologue et d'épilogue ne correspondent pas toujours exactement. Dans ce cas, il se peut que le tableau des codes de déroulement doive contenir plusieurs séquences de codes. Pour déterminer à quel décalage commencer le traitement des codes, suivez cette logique :

1. Si le déroulement démarre dans le corps de la fonction, commencez à exécuter les codes de déroulement à l'index 0 et continuez jusqu'à ce qu'un opcode de fin soit atteint.

2. Si le déroulement démarre dans un épilogue, utilisez l'index de démarrage propre à l'épilogue fourni par la portée de l'épilogue. Calculez le nombre d'octets qui séparent le compteur de programme (PC) du début de l'épilogue. Parcourez les codes de déroulement jusqu'à ce que toutes les instructions déjà exécutées soient prises en compte. Exécutez la séquence de déroulement à partir de ce point.

3. Si le déroulement démarre dans le prologue, partez de l'index 0 dans les codes de déroulement. Calculez la longueur du code de prologue à partir de la séquence, puis calculez le nombre d'octets qui séparent le compteur de programme (PC) de la fin du prologue. Parcourez les codes de déroulement jusqu'à ce que toutes les instructions non exécutées soient prises en compte. Exécutez la séquence de déroulement à partir de ce point.

Les codes de déroulement du prologue doivent toujours être les premiers dans le tableau. Ce sont aussi les codes généralement utilisés dans les déroulements qui démarre dans le corps. Les séquences de codes propres à l'épilogue doivent suivre immédiatement la séquence de codes du prologue.

### <a name="function-fragments"></a>Fragments de fonction

Pour l'optimisation de code, il peut être utile de scinder une fonction en plusieurs parties discontinues. Dès lors, chaque fragment de fonction nécessite son propre enregistrement .pdata (et éventuellement .xdata) distinct.

En supposant que le prologue de la fonction se trouve au début de la fonction et qu'il ne peut pas être scindé, il existe quatre cas de fragments de fonction :

- un prologue uniquement ; tous les épilogues se trouvent dans d'autres fragments ;

- un prologue et un ou plusieurs épilogues ; épilogues supplémentaires dans d'autres fragments ;

- pas de prologue ni d'épilogues ; un prologue et un ou plusieurs épilogues dans d'autres fragments ;

- des épilogues uniquement ; un prologue et éventuellement des épilogues supplémentaires dans d'autres fragments.

Dans le premier cas, seul le prologue doit être décrit. Cela est possible dans une forme .pdata compacte en décrivant le prologue normalement et en spécifiant un *Ret* valeur 3 pour n’indiquer aucun épilogue. Dans la forme .xdata complète, cela peut se faire en fournissant les codes de déroulement du prologue à l'index 0 comme d'habitude, et en spécifiant un nombre d'épilogues égal à 0.

Le deuxième cas s'apparente tout simplement à une fonction normale. Si le fragment contient un seul épilogue et qu'il se trouve à la fin du fragment, un enregistrement .pdata compact peut être utilisé. Sinon, il convient d'utiliser un enregistrement .xdata complet. Gardez à l'esprit que les décalages spécifiés pour le début de l'épilogue sont fonction du début du fragment, et non du début initial de la fonction.

Les troisième et quatrième cas sont des variantes des premier et deuxième cas, respectivement, sauf qu'ils ne contiennent pas de prologue. Dans ces situations, du code est censé précéder l'épilogue et est considéré comme faisant partie du corps de la fonction, dont le déroulement procède normalement de l'annulation des effets du prologue. Ces cas doivent ainsi être encodés avec un pseudo-prologue, qui décrit la façon dont le déroulement s'opère à partir du corps, mais qui est considéré comme étant de longueur nulle au moment de déterminer si un déroulement partiel doit être effectué au début du fragment. Ce pseudo-prologue peut aussi être décrit en utilisant les mêmes codes de déroulement que l'épilogue, car on peut supposer qu'ils effectuent des opérations équivalentes.

Dans les troisième et quatrième cas, la présence d’un pseudo-prologue est spécifiée en affectant la *indicateur* champ de l’enregistrement .pdata compact à 2, ou en définissant le *F* indicateur dans l’en-tête .xdata à 1. Dans les deux cas, la recherche d'un déroulement de prologue partiel est ignorée et tous les déroulements non liés aux épilogues sont considérés comme complets.

#### <a name="large-functions"></a>Grandes fonctions

Les fragments permettent de décrire les fonctions dont la taille dépasse la limite de 512 Ko imposée par les champs de bit de l'en-tête .xdata. Pour décrire une fonction très volumineuse, il suffit de la décomposer en fragments inférieurs à 512 Ko. Chaque fragment doit être ajusté afin qu'il ne divise pas un épilogue en plusieurs parties.

Seul le premier fragment de la fonction contient un prologue ; tous les autres fragments sont marqués comme n'ayant pas de prologue. Selon le nombre d'épilogues, chaque fragment peut contenir aucun ou plusieurs épilogues. Ne perdez pas de vue que chaque portée d'épilogue d'un fragment spécifie son décalage de départ par rapport au début du fragment, et non au début de la fonction.

Si un fragment ne contient ni prologue ni épilogue, il a toujours besoin de son propre enregistrement .pdata (et éventuellement .xdata) pour décrire le mode de déroulement à partir du corps de la fonction.

#### <a name="shrink-wrapping"></a>Emballage par rétraction

Est un cas spécial plus complexe de fragments de fonction *rétraction*, une technique pour différer le Registre enregistre à partir du début de la fonction à plus tard dans la fonction, pour optimiser les cas simples qui ne nécessitent pas l’enregistrement du Registre. D'un côté, une région externe alloue l'espace de la pile mais enregistre un ensemble minimal de registres et d'un autre, une région interne enregistre et restaure des registres supplémentaires.

```asm
ShrinkWrappedFunction
     push   {r4, lr}          ; A: save minimal non-volatiles
     sub    sp, sp, #0x100    ; A: allocate all stack space up front
     ...                     ; A:
     add    r0, sp, #0xE4     ; A: prepare to do the inner save
     stm    r0, {r5-r11}      ; A: save remaining non-volatiles
     ...                     ; B:
     add    r0, sp, #0xE4     ; B: prepare to do the inner restore
     ldm    r0, {r5-r11}      ; B: restore remaining non-volatiles
     ...                     ; C:
     pop    {r4, pc}          ; C:
```

Les fonctions emballées par rétractation sont en principe censées préallouer l'espace pour les enregistrements de registre supplémentaires dans le prologue normal et procéder ensuite aux enregistrements de registres à l'aide de `str` ou `stm` à la place de `push`. Toutes les manipulations de pointeur de pile sont ainsi maintenues dans le prologue initial de la fonction.

La fonction emballée par rétraction prise pour exemple doit être divisée en trois régions, qui correspondent aux lettres A, B et C dans les commentaires. La première région A s'étend du début de la fonction jusqu'à la fin des enregistrements non volatifs supplémentaires. Un enregistrement .pdata ou .xdata doit être construit pour indiquer la présence d'un prologue et l'absence d'épilogues dans ce fragment.

La région B intermédiaire obtient son propre enregistrement .pdata ou .xdata qui décrit un fragment qui n'a ni prologue ni épilogue. Cependant, des codes de déroulement doivent toujours être présents pour cette région, car elle est considérée comme un corps de fonction. Les codes doivent décrire un prologue composite qui représente à la fois les registres initiaux enregistrés dans le prologue de la région A et les registres supplémentaires enregistrés avant d'entrer dans la région B, comme s'ils étaient générés par une même séquence d'opérations.

Les enregistrements de registres de la région B ne peuvent pas être considérés comme un « prologue interne », car le prologue composite décrit pour la région B doit décrire à la fois le prologue de la région A et les registres supplémentaires enregistrés. S'il était indiqué que le fragment B contenait un prologue, la taille de ce prologue serait aussi induite par les codes de déroulement. Or, il n'existe aucun moyen de décrire le prologue composite qui autorise un mappage un-à-un avec les opcodes qui enregistrent uniquement les registres supplémentaires.

Les enregistrements de registres supplémentaires doivent être considérés comme faisant partie de la région A, car tant qu'ils n'ont pas été menés à bien, le prologue composite ne décrit pas avec précision l'état de la pile.

La dernière région C obtient son propre enregistrement .pdata ou .xdata, décrivant un fragment sans prologue, mais avec un épilogue.

Une autre approche peut aussi fonctionner si les manipulations de la pile réalisées avant l'entrée dans la région B peuvent être réduites à une seule instruction :

```asm
ShrinkWrappedFunction
     push   {r4, lr}          ; A: save minimal non-volatile registers
     sub    sp, sp, #0xE0     ; A: allocate minimal stack space up front
     ...                     ; A:
     push   {r4-r9}           ; A: save remaining non-volatiles
     ...                     ; B:
     pop    {r4-r9}           ; B: restore remaining non-volatiles
     ...                     ; C:
     pop    {r4, pc}          ; C: restore non-volatile registers
```

Ce qui importe ici, c'est qu'à chaque limite d'instruction, la pile est entièrement cohérente par rapport aux codes de déroulement de la région. Si un déroulement se produit avant le push interne de cet exemple, il est considéré comme faisant partie de la région A et seul le prologue de la région A prologue fait l'objet d'un déroulement. Si le déroulement se produit après le push interne, il est considéré comme partie de la région B, qui n’a pas de prologue, mais des codes de déroulement qui décrivent le push interne et le prologue initial de région une logique similaire A. contient au POP interne.

### <a name="encoding-optimizations"></a>Encodage d'optimisations

Du fait de la richesse des codes de déroulement et de leur aptitude à exploiter des formes de données compactes et développées, il est possible d'optimiser l'encodage de diverses manières afin de réduire davantage l'espace. En ayant largement recours à ces techniques, la surcharge nette induite par la description des fonctions et des fragments à l'aide de codes de déroulement peut être assez minime.

L'optimisation la plus importante consiste à faire attention à ne pas confondre les limites de prologue/épilogue en vue d'un déroulement avec les limites de prologue/épilogue du point de vue du compilateur. Les limites de déroulement peuvent être réduites et resserrées pour améliorer l'efficacité. Par exemple, un prologue peut contenir du code après la configuration de la pile pour effectuer des vérifications supplémentaires. Mais une fois que toutes les manipulations de pile ont été réalisées, il n'est pas utile d'encoder d'autres opérations et tout ce qui se trouve au-delà peut être supprimé du prologue de déroulement.

La même règle s'applique à la longueur des fonctions. Si des données (par exemple, un pool de littéraux) suivent l'épilogue d'une fonction, elles ne doivent pas être prises en compte dans la longueur de la fonction. En réduisant la fonction au seul code intégré à la fonction, il y a bien plus de chances que l'épilogue se trouve à la toute fin et compact. Un enregistrement pdata peut être utilisé.

Dans un prologue, dès lors que le pointeur de pile est enregistré dans un autre registre, il n'y a généralement pas besoin d'enregistrer d'autres opcodes. Pour dérouler la fonction, la première chose à faire est de récupérer le pointeur de pile auprès du registre enregistré, ce qui évite que les opérations ultérieures aient un impact sur le déroulement.

Les épilogues à une instruction n'ont pas du tout besoin d'être encodées, ni en tant que portées ni en tant que codes de déroulement. Si un déroulement se produit avant que l'instruction soit exécutée, on peut supposer qu'elle provient du corps de la fonction et que la simple exécution des codes de déroulement de prologue suffit. Si le déroulement se produit après l'exécution de l'instruction unique, elle se produit de fait dans une autre région.

Les épilogues à plusieurs instructions n'ont pas besoin d'encoder la première instruction de l'épilogue, pour la même raison que précédemment : si le déroulement se produit avant l'exécution de l'instruction, un déroulement de prologue complet suffit. Si le déroulement se produit après cette instruction, seules les opérations suivantes doivent être prises en considération.

La réutilisation de code de déroulement doit être insistante. L'index spécifié par chaque portée d'épilogue pointe vers un point de départ arbitraire dans le tableau des codes de déroulement. Il ne doit pas nécessairement pointer vers le début d'une séquence précédente ; il peut pointer vers le milieu. La meilleure approche ici consiste à générer la séquence de codes souhaitée et de rechercher une correspondance d'octets exacte dans le pool de séquences déjà encodé et à utiliser une correspondance exacte comme point de départ de la réutilisation.

Si, une fois que les épilogues à une instruction ont été ignorés, il ne reste plus aucun épilogue, envisagez d'utiliser un formulaire .pdata compact ; cela devient bien plus probable en l'absence d'épilogue.

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

   - *Début de la fonction RVA* = 0x000535F8 (= 0x004535F8-0 x 00400000)

- Mot 1

   - *Indicateur* = 1, indiquant les formats de prologue et épilogue canoniques

   - *Longueur de la fonction* = 0 x 31 (= 0 x 62/2)

   - *RET* = 1, indiquant une retour de branche de 16 bits

   - *H* = 0, indiquant les paramètres n’étaient pas hébergés.

   - *R*= 0 et *Reg* = 1, indiquant un push/pop de r4-r5

   - *L* = 0, n’indiquant aucune LR sauvegarde/restauration

   - *C* = 0, n’indiquant aucun chaînage de frames

   - *Ajuster la pile* = 0, ce qui indique aucun ajustement de pile

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

   - *Début de la fonction RVA* = 0x000533AC (= 0x004533AC-0 x 00400000)

- Mot 1

   - *Indicateur* = 1, indiquant les formats de prologue et épilogue canoniques

   - *Longueur de la fonction* = 0 x 35 (= 0x6A/2)

   - *RET* = 0, indiquant {un pc} pop retour

   - *H* = 0, indiquant les paramètres n’étaient pas hébergés.

   - *R*= 0 et *Reg* = 3, indiquant les push/pop de r4-r7

   - *L* = 1, indiquant LR a été enregistré/restauré

   - *C* = 0, n’indiquant aucun chaînage de frames

   - *Pile ajuster* = 3 (= 0x0C/4)

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

   - *Début de la fonction RVA* = 0x00053988 (= 0x00453988-0 x 00400000)

- Mot 1

   - *Indicateur* = 1, indiquant les formats de prologue et épilogue canoniques

   - *Longueur de la fonction* = 0x2A (= 0 x 54/2)

   - *RET* = 0, indiquant un {pc} pop-style de retour (dans ce cas un ldr pc, [sp], 0 x 14 # retour)

   - *H* = 1, indiquant les paramètres étaient hébergés

   - *R*= 0 et *Reg* = 2, indiquant les push/pop de r4-r6

   - *L* = 1, indiquant LR a été enregistré/restauré

   - *C* = 0, n’indiquant aucun chaînage de frames

   - *Ajuster la pile* = 0, ce qui indique aucun ajustement de pile

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

   - *Début de la fonction RVA* = 0x000592F4 (= 0x004592F4-0 x 00400000)

- Mot 1

   - *Indicateur* = 0, indiquant un enregistrement .xdata (nécessaire en raison des multiples épilogues)

   - *.XData adresse* -0 x 00400000

.xdata (variable, 6 mots) :

- Mot 0

   - *Longueur de la fonction* = 0x0001A3 (= 0x000346/2)

   - *Vers* = 0, ce qui indique la première version de xdata

   - *X* = 0, n’indiquant aucune donnée d’exception

   - *E* = 0, indiquant une liste de portées d’épilogue

   - *F* = 0, indiquant une description complète de la fonction, prologue compris

   - *Nombre d’épilogue* = 0 x 04, indiquant les 4 portées d’épilogue totales

   - *Les mots de code* = 0 x 01, indiquant un mot de 32 bits de codes de déroulement

- Mots 1 à 4, décrivant 4 portées d'épilogue à 4 emplacements. À chaque portée correspond un ensemble commun de codes de déroulement, partagé avec le prologue, au niveau du décalage 0x00, et inconditionnel, spécifiant la condition 0x0E (toujours).

- Codes de déroulement, commençant au Mot 5 : (partagé entre le prologue et l'épilogue)

   - Code de déroulement 0 = 0x06 : sp += (6 << 2)

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

   - *Début de la fonction RVA* = 0x00085A20 (= 0x00485A20-0 x 00400000)

- Mot 1

   - *Indicateur* = 0, indiquant un enregistrement .xdata (nécessaire en raison des multiples épilogues)

   - *.XData adresse* -0 x 00400000

.xdata (variable, 3 mots) :

- Mot 0

   - *Longueur de la fonction* = 0x0001A3 (= 0x000346/2)

   - *Vers* = 0, ce qui indique la première version de xdata

   - *X* = 0, n’indiquant aucune donnée d’exception

   - *E* = 0, indiquant une liste de portées d’épilogue

   - *F* = 0, indiquant une description complète de la fonction, prologue compris

   - *Nombre d’épilogue* = 0 x 001, qui indique la portée d’épilogue totales 1

   - *Les mots de code* = 0 x 01, indiquant un mot de 32 bits de codes de déroulement

- Mot 1 : portée d'épilogue au niveau du décalage 0xC6 (= 0x18C/2), index du code de déroulement de départ à 0x00, avec une condition de 0x0E (toujours)

- Codes de déroulement, commençant au Mot 2 : (partagé entre le prologue et l'épilogue)

   - Code de déroulement 0 = 0xC6 : sp = r6

   - Code de déroulement 1 = 0xDC : pop {r4-r8, lr}

   - Code de déroulement 2 = 0x04 : sp += (4 << 2)

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

   - *Début de la fonction RVA* = 0x00088C24 (= 0x00488C24-0 x 00400000)

- Mot 1

   - *Indicateur* = 0, indiquant un enregistrement .xdata (nécessaire en raison des multiples épilogues)

   - *.XData adresse* -0 x 00400000

.xdata (variable, 5 mots) :

- Mot 0

   - *Longueur de la fonction* = 0x000027 (= 0x00004E/2)

   - *Vers* = 0, ce qui indique la première version de xdata

   - *X* = 1, indiquant les données d’exception présentes

   - *E* = 1, indiquant un épilogue unique

   - *F* = 0, indiquant une description complète de la fonction, prologue compris

   - *Nombre d’épilogue* = 0 x 00, indiquant les codes de déroulement d’épilogue commencent au décalage 0 x 00

   - *Les mots de code* = 0 x 02, indiquant les deux mots de 32 bits de codes de déroulement

- Codes de déroulement, commençant au Mot 1 :

   - Code de déroulement 0 = 0xC7 : sp = r7

   - Code de déroulement 1 = 0x05 : sp += (5 << 2)

   - Code de déroulement 2 = 0xED/0x90 : pop {r4, r7, lr}

   - Code de déroulement 4 = 0xFF : fin

- Mot 3 spécifie un gestionnaire d’exceptions = 0x0019A7ED (= 0x0059A7ED - 0 x 00400000)

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

   - *Début de la fonction RVA* = 0x00088C72 (= 0x00488C72-0 x 00400000)

- Mot 1

   - *Indicateur* = 1, indiquant les formats de prologue et épilogue canoniques

   - *Longueur de la fonction* = 0x0B (= 0 x 16/2)

   - *RET* = 0, indiquant {un pc} pop retour

   - *H* = 0, indiquant les paramètres n’étaient pas hébergés.

   - *R*= 0 et *Reg* = 7, n’indiquant aucun registre ont été enregistré/restauré

   - *L* = 1, indiquant LR a été enregistré/restauré

   - *C* = 0, n’indiquant aucun chaînage de frames

   - *Ajuster la pile* = 1, ce qui indique un ajustement de pile 1 × 4 octets

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble des conventions ABI ARM](../build/overview-of-arm-abi-conventions.md)  
[Problèmes courants de migration ARM Visual C++](../build/common-visual-cpp-arm-migration-issues.md)  