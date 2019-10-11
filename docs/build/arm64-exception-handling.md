---
title: Gestion des exceptions ARM64
ms.date: 11/19/2018
ms.openlocfilehash: b4f9a5d6f86f8b88ef42525e6a9bb1b4071585ce
ms.sourcegitcommit: a9f1a1ba078c2b8c66c3d285accad8e57dc4539a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2019
ms.locfileid: "72037748"
---
# <a name="arm64-exception-handling"></a>Gestion des exceptions ARM64

Windows sur ARM64 utilise le même mécanisme de gestion structurée des exceptions pour les exceptions générées par le matériel asynchrones et les exceptions générées par les logiciels synchrones. Les gestionnaires d'exceptions propres aux langages s'appuient sur la gestion des exceptions structurées Windows en utilisant des fonctions d'assistance de langage. Ce document décrit la gestion des exceptions dans Windows sur ARM64, ainsi que les applications auxiliaires de langage utilisées par le code généré par l’assembleur Microsoft ARM et le compilateur MSVC.

## <a name="goals-and-motivation"></a>Objectifs et motivation

L’exception qui déroule les conventions de données, et cette description, sont destinées à :

1. Fournissez suffisamment de description pour permettre le déroulement sans la détection de code dans tous les cas.

   - L’analyse du code requiert que le code soit paginé dans. Cela évite le déroulement dans certaines circonstances où il est utile (traçage, échantillonnage, débogage).

   - L’analyse du code est complexe. le compilateur doit veiller à générer uniquement des instructions que le décodeur est capable de décoder.

   - Si le déroulement ne peut pas être entièrement décrit à l’aide de codes de déroulement, dans certains cas, il doit revenir au décodage d’instruction. Cela augmente la complexité globale et, idéalement, est évité.

1. Prendre en charge le déroulement dans le prologue intermédiaire et l’épilogue intermédiaire.

   - Le déroulement est utilisé dans Windows pour plus que la gestion des exceptions. il est donc essentiel que nous puissions effectuer un déroulement précis même quand il se trouve au milieu d’une séquence de code de prologue ou d’épilogue.

1. Occupent une quantité minimale d’espace.

   - Les codes de déroulement ne doivent pas être agrégés pour augmenter considérablement la taille binaire.

   - Étant donné que les codes de déroulement sont susceptibles d’être verrouillés en mémoire, un faible encombrement garantit une surcharge minimale pour chaque binaire chargé.

## <a name="assumptions"></a>Assumptions (Hypothèses)

Voici les hypothèses prises dans la description de la gestion des exceptions :

1. Les journaux et les épilogues ont tendance à refléter l’un ou l’autre. En tirant parti de cette caractéristique commune, la taille des métadonnées requises pour décrire le déroulement peut être sensiblement réduite. Dans le corps de la fonction, il n’est pas important de savoir si les opérations du prologue sont annulées ou si les opérations de l’épilogue sont exécutées de manière anticipée. Les deux doivent produire des résultats identiques.

1. Les fonctions ont tendance à être relativement petites. Plusieurs optimisations de l’espace s’appuient sur cette valeur pour obtenir le compactage de données le plus efficace.

1. Il n’y a pas de code conditionnel dans épilogues.

1. Registre de pointeur de frame dédié : Si le SP est enregistré dans un autre registre (x29) dans le prologue, ce registre reste intact tout au long de la fonction, afin que le SP d’origine puisse être récupéré à tout moment.

1. À moins que le SP ne soit enregistré dans un autre registre, toute manipulation du pointeur de pile se produit strictement dans le prologue et l’épilogue.

1. La disposition des frames de pile est organisée comme décrit dans la section suivante.

## <a name="arm64-stack-frame-layout"></a>Disposition des frames de pile ARM64

(media/arm64-exception-handling-stack-frame.png "disposition du frame de pile") de la ![disposition Frame Frame]

Pour les fonctions chaînées de frame, les paires FP et LR peuvent être enregistrées à n’importe quel emplacement dans la zone de variables locales en fonction des considérations relatives à l’optimisation. L’objectif est d’optimiser le nombre de variables locales qui peuvent être atteintes par une seule instruction basée sur un pointeur de frame (x29) ou un pointeur de pile (SP). Toutefois, pour les fonctions `alloca`, il doit être chaîné et x29 doit pointer vers le bas de la pile. Pour permettre une meilleure couverture du mode de Registre-paire-adressage, les zones d’enregistrement des registres non volatiles sont positionnées en haut de la pile de la zone locale. Voici des exemples qui illustrent plusieurs des séquences de prologue les plus efficaces. Par souci de clarté et de meilleure localité de cache, l’ordre de stockage des registres enregistrés par l’appelé dans tous les projournals canoniques est dans l’ordre croissant. `#framesz` représente la taille de la pile entière (à l’exception de la zone allouée). `#localsz` et `#outsz` indiquent la taille de la zone locale (y compris la zone d’enregistrement pour la paire \<x29, LR >) et la taille du paramètre sortant, respectivement.

1. Chained, #localsz \<= 512

    ```asm
        stp    x19,x20,[sp,#-96]!        // pre-indexed, save in 1st FP/INT pair
        stp    d8,d9,[sp,#16]            // save in FP regs (optional)
        stp    x0,x1,[sp,#32]            // home params (optional)
        stp    x2,x3,[sp,#48]
        stp    x4,x5,[sp,#64]
        stp    x6,x7,[sp,#72]
        stp    x29,lr,[sp,#-localsz]!   // save <x29,lr> at bottom of local area
        mov    x29,sp                   // x29 points to bottom of local
        sub    sp,sp,#outsz             // (optional for #outsz != 0)
    ```

1. Chaîné, #localsz > 512

    ```asm
        stp    x19,x20,[sp,#-96]!        // pre-indexed, save in 1st FP/INT pair
        stp    d8,d9,[sp,#16]            // save in FP regs (optional)
        stp    x0,x1,[sp,#32]            // home params (optional)
        stp    x2,x3,[sp,#48]
        stp    x4,x5,[sp,#64]
        stp    x6,x7,[sp,#72]
        sub    sp,sp,#(localsz+outsz)   // allocate remaining frame
        stp    x29,lr,[sp,#outsz]       // save <x29,lr> at bottom of local area
        add    x29,sp,#outsz            // setup x29 points to bottom of local area
    ```

1. Non chaîné, fonctions feuille (LR non enregistrées)

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]
        str    x23,[sp,#32]
        stp    d8,d9,[sp,#40]           // save FP regs (optional)
        stp    d10,d11,[sp,#56]
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   Toutes les variables locales sont accessibles en fonction du SP. \<x29, LR > pointe vers le frame précédent. Pour la taille de trame \< = 512, « Sub SP,... » peut être optimisé si la zone enregistrée regs est déplacée en bas de la pile. L’inconvénient de cette approche est qu’elle n’est pas cohérente avec les autres dispositions ci-dessus et que les regs enregistrés prennent part à la plage pour le mode d’adressage de décalage pré-et-regs et après indexation.

1. Fonctions non-feuille et non chaînées (la LR est enregistrée dans la zone enregistrée int)

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]         // ...
        stp    x23,lr,[sp,#32]          // save last Int reg and lr
        stp    d8,d9,[sp,#48]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,#64]         // ...
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   Ou, avec un nombre pair de registres int enregistrés,

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]         // ...
        str    lr,[sp,#32]              // save lr
        stp    d8,d9,[sp,#40]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,#56]         // ...
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   Uniquement x19 enregistrées :

    ```asm
        sub    sp,sp,#16                // reg save area allocation*
        stp    x19,lr,[sp]              // save x19, lr
        sub    sp,sp,#(framesz-16)      // allocate the remaining local area
    ```

   \* l’allocation de la zone d’enregistrement reg n’est pas repliée dans le STP, car un STP reg-LR préconfiguré ne peut pas être représenté avec les codes de déroulement.

   Toutes les variables locales sont accessibles en fonction du SP. @no__t > 0x29 pointe vers le frame précédent.

1. Chained, #framesz \<= 512, #outsz = 0

    ```asm
        stp    x29,lr,[sp,#-framesz]!       // pre-indexed, save <x29,lr>
        mov    x29,sp                       // x29 points to bottom of stack
        stp    x19,x20,[sp,#(framesz-32)]   // save INT pair
        stp    d8,d9,[sp,#(framesz-16)]     // save FP pair
    ```

   En comparaison avec le prologue #1 ci-dessus, l’avantage est que toutes les instructions Save Register sont prêtes à être exécutées juste après la seule pile d’allocation d’instruction. Par conséquent, il n’existe pas d’anti-dépendance sur le SP qui empêche le parallélisme au niveau des instructions.

1. Chaîné, taille de cadre > 512 (facultatif pour les fonctions sans alloca)

    ```asm
        stp    x29,lr,[sp,#-80]!            // pre-indexed, save <x29,lr>
        stp    x19,x20,[sp,#16]             // save in INT regs
        stp    x21,x22,[sp,#32]             // ...
        stp    d8,d9,[sp,#48]               // save in FP regs
        stp    d10,d11,[sp,#64]
        mov    x29,sp                       // x29 points to top of local area
        sub    sp,sp,#(framesz-80)          // allocate the remaining local area
    ```

   À des fins d’optimisation, x29 peut être placé à n’importe quelle position dans la zone locale pour offrir une meilleure couverture pour les modes « reg-pair » et d’adressage de décalage antérieur à/post-Indexed. Les variables locales sous les pointeurs de frame sont accessibles en fonction du SP.

1. Chaîné, taille de trame > 4K, avec ou sans alloca (),

    ```asm
        stp    x29,lr,[sp,#-80]!            // pre-indexed, save <x29,lr>
        stp    x19,x20,[sp,#16]             // save in INT regs
        stp    x21,x22,[sp,#32]             // ...
        stp    d8,d9,[sp,#48]               // save in FP regs
        stp    d10,d11,[sp,#64]
        mov    x29,sp                       // x29 points to top of local area
        mov    x15,#(framesz/16)
        bl     __chkstk
        sub    sp,sp,x15,lsl#4              // allocate remaining frame
                                            // end of prolog
        ...
        sub    sp,sp,#alloca                // more alloca() in body
        ...
                                            // beginning of epilog
        mov    sp,x29                       // sp points to top of local area
        ldp    d10,d11,[sp,#64]
        ...
        ldp    x29,lr,[sp],#80              // post-indexed, reload <x29,lr>
    ```

## <a name="arm64-exception-handling-information"></a>Informations de gestion des exceptions ARM64

### <a name="pdata-records"></a>enregistrements. pdata

Les enregistrements. pdata sont un tableau ordonné d’éléments de longueur fixe qui décrivent chaque fonction de manipulation de pile dans un fichier binaire PE. Notez attentivement l’expression « manipulation de pile » : les fonctions feuille qui ne nécessitent pas de stockage local et qui n’ont pas besoin d’enregistrer/de restaurer des registres non volatiles ne nécessitent pas d’enregistrement. pdata ; celles-ci doivent être explicitement omises pour économiser de l’espace. Un déroulement de l’une de ces fonctions peut simplement obtenir l’adresse de retour à partir de LR pour remonter à l’appelant.

Chaque enregistrement. pdata pour ARM64 a une longueur de 8 octets. Le format général de chaque enregistrement place l’adresse RVA 32 bits de la fonction Start dans le premier mot, suivi d’un second avec qui contient soit un pointeur vers un bloc. XData de longueur variable, soit un mot compressé qui décrit une séquence de déroulement de fonction canonique.

mise en page de l’enregistrement ![. pdata]disposition(media/arm64-exception-handling-pdata-record.png ". pdata")

Les champs sont les suivants :

- **RVA Start Function** est l’adresse RVA 32 bits du début de la fonction.

- L' **indicateur** est un champ de 2 bits qui indique comment interpréter les 30 bits restants du deuxième mot. pData. Si l' **indicateur** a la valeur 0, les bits restants forment un **RVA d’informations sur l’exception** (avec les deux bits de poids faible implicitement 0). Si l' **indicateur** est différent de zéro, les bits restants forment une structure de **données de déroulement compressées** .

- Les **informations d’exception RVA** sont l’adresse de la structure d’informations sur les exceptions de longueur variable, stockée dans la section. XData. Ces données doivent être alignées sur 4 octets.

- Les **données de déroulement** compressées sont une description compressée des opérations nécessaires au déroulement d’une fonction, en supposant une forme canonique. Dans ce cas, aucun enregistrement .xdata n'est nécessaire.

### <a name="xdata-records"></a>enregistrements. XData

Quand le format de déroulement compressé ne suffit pas à décrire le déroulement d'une fonction, un enregistrement .xdata de longueur variable doit être créé. L'adresse de cet enregistrement est stockée dans le deuxième mot de l'enregistrement .pdata. Le format du. XData est un ensemble de mots condensé de longueur variable :

![. XData disposition]de l’enregistrement(media/arm64-exception-handling-xdata-record.png ". XData")

Ces données sont réparties en quatre sections :

1. En-tête 1 ou 2-Word décrivant la taille globale de la structure et fournissant les données de fonction clés. Le deuxième mot est présent uniquement si les champs **nombre d’épilogues** et **mots de code** ont la valeur 0. Il s’agit des champs de bits dans l’en-tête :

   a. La **longueur de fonction** est un champ de 18 bits indiquant la longueur totale de la fonction en octets, divisée par 4. Si une fonction est supérieure à 1M, plusieurs enregistrements pData et XData doivent être utilisés pour décrire la fonction. Pour plus d’informations, consultez la section [fonctions volumineuses](#large-functions) .

   b. **Vers** est un champ de 2 bits décrivant la version des XData restantes. À partir de cet article, seule la version 0 est définie et, par conséquent, les valeurs de 1-3 ne sont pas autorisées.

   c. **X** est un champ de 1 bit indiquant la présence (1) ou l’absence (0) de données d’exception.

   d. **E** est un champ de bits qui indique que les informations décrivant un épilogue unique sont empaquetées dans l’en-tête (1) au lieu d’exiger des mots d’étendue supplémentaires plus tard (0).

   e. Le **nombre d’épilogues** est un champ de 5 bits qui a deux significations, en fonction de l’état du bit **E** :

      1. Si **E** est défini sur 0 : il spécifie le nombre total de portées d’épilogue décrites dans la section 2. S’il existe plus de 31 portées dans la fonction, le champ **code** Words doit avoir la valeur 0 pour indiquer qu’un mot d’extension est nécessaire.

      2. Si **E** est défini sur 1, ce champ spécifie l’index du premier code de déroulement qui décrit l’un et l’épilogue uniquement.

   f. Les **mots de code** sont un champ de 5 bits qui spécifie le nombre de mots de 32 bits nécessaires pour contenir tous les codes de déroulement de la section 3. Si plus de 31 mots sont requis (par exemple, plus de 124 octets de code de déroulement), ce champ doit avoir la valeur 0 pour indiquer qu’un mot d’extension est nécessaire.

   g. Le nombre **étendu d’épilogues** et les **mots de code étendu** sont des champs 16 bits et 8 bits, respectivement, qui fournissent plus d’espace pour l’encodage d’un nombre anormalement élevé de épilogues ou d’un nombre anormalement élevé de mots de code de déroulement. Le mot d’extension contenant ces champs est présent uniquement si les champs **nombre d’épilogues** et **mots de code** du premier mot d’en-tête ont la valeur 0.

1. Après l’en-tête et l’en-tête étendu facultatif décrits ci-dessus, si le **nombre d’épilogues** n’est pas égal à zéro, est une liste d’informations sur les portées d’épilogue, compressées en un mot, et stockées par ordre de décalage de début d’incrémentation. Chaque étendue contient les bits suivants :

   a. L' **offset de début d’épilogue** est un champ de 18 bits décrivant le décalage en octets, divisé par 4, de l’épilogue par rapport au début de la fonction

   b. **Res** est un champ de 4 bits réservé pour un développement futur. Il doit avoir la valeur 0.

   c. L' **index de début d’épilogue** est un champ de 10 bits (2 plus bits que les **mots de code étendus**) indiquant l’index d’octets du premier code de déroulement qui décrit cet épilogue.

1. Une fois que la liste des étendues d’épilogue est un tableau d’octets qui contiennent des codes de déroulement, décrits en détail dans une section ultérieure. Ce tableau est rempli à la fin jusqu'à la limite du mot complet le plus proche. Les codes de déroulement sont écrits dans ce tableau, en commençant par le plus proche du corps de la fonction, en se déplaçant vers les bords de la fonction. Les octets de chaque code de déroulement sont stockés par ordre de primauté des octets de poids fort, afin de pouvoir être récupérés directement, en commençant par l’octet le plus significatif en premier, qui identifie l’opération et la longueur du reste du code.

1. Enfin, après le code de déroulement bytes, si le bit **X** dans l’en-tête a la valeur 1, les informations du gestionnaire d’exceptions sont fournies. Il s’agit d’un **RVA de gestionnaire d’exceptions** unique qui fournit l’adresse du gestionnaire d’exceptions lui-même, suivi immédiatement d’une quantité variable de données requises par le gestionnaire d’exceptions.

L’enregistrement. XData ci-dessus est conçu de telle sorte qu’il est possible de récupérer les 8 premiers octets et de calculer la taille complète de l’enregistrement (moins la longueur des données d’exception de taille variable qui suit). L’extrait de code suivant calcule la taille de l’enregistrement :

```cpp
ULONG ComputeXdataSize(PULONG *Xdata)
{
    ULONG EpilogScopes;
    ULONG Size;
    ULONG UnwindWords;

    if ((Xdata[0] >> 27) != 0) {
        Size = 4;
        EpilogScopes = (Xdata[0] >> 22) & 0x1f;
        UnwindWords = (Xdata[0] >> 27) & 0x0f;
    } else {
        Size = 8;
        EpilogScopes = Xdata[1] & 0xffff;
        UnwindWords = (Xdata[1] >> 16) & 0xff;
    }

    Size += 4 * EpilogScopes;
    Size += 4 * UnwindWords;
    if (Xdata[0] & (1 << 20)) {
        Size += 4;        // exception handler RVA
    }
    return Size;
}
```

Il convient de noter que, bien que le prologue et chaque épilogue possèdent son propre index dans les codes de déroulement, la table est partagée entre eux, et il est tout à fait possible (et non pas totalement rare) qu’ils puissent tous partager les mêmes codes (Voir l’exemple 2 de la section exemples bel). en anglais). Les writers de compilateur doivent optimiser pour ce cas, en particulier parce que l’index le plus grand pouvant être spécifié est 255, ce qui limite le nombre total de codes de déroulement pour une fonction particulière.

### <a name="unwind-codes"></a>Codes de déroulement

Le tableau des codes de déroulement est un pool de séquences qui décrivent exactement comment annuler les effets du prologue, dans l’ordre dans lequel les opérations doivent être annulées. Les codes de déroulement peuvent être considérés comme un mini ensemble d’instructions, codé sous la forme d’une chaîne d’octets. Une fois l’exécution terminée, l’adresse de retour à la fonction appelante se trouve dans le registre GD, et tous les registres non volatils sont restaurés sur leurs valeurs au moment de l’appel de la fonction.

S’il est garanti que les exceptions ne se produisent que dans le corps d’une fonction (et jamais avec un prologue ou un épilogue), une seule séquence est nécessaire. Toutefois, le modèle de déroulement Windows requiert que nous puissions effectuer une dérouler à partir d’un prologue ou d’un épilogue partiellement exécuté. Pour répondre à cette exigence, les codes de déroulement ont été soigneusement conçus de manière à ce qu’ils mappent sans ambiguïté 1:1 à chaque opcode approprié dans le prologue et l’épilogue. Cela a plusieurs conséquences :

1. En comptant le nombre de codes de déroulement, il est possible de calculer la longueur du prologue et d’épilogue.

1. En comptant le nombre d’instructions au-delà du début d’une portée d’épilogue, il est possible d’ignorer le nombre équivalent de codes de déroulement et d’exécuter le reste d’une séquence pour terminer le déroulement partiellement exécuté par l’épilogue.

1. En comptant le nombre d’instructions avant la fin du prologue, il est possible d’ignorer le nombre équivalent de codes de déroulement et d’exécuter le reste de la séquence pour annuler uniquement les parties du prologue dont l’exécution est terminée.

Les codes de déroulement sont encodés selon le tableau ci-dessous. Tous les codes de déroulement sont un octet unique/double, à l’exception de celui qui alloue une énorme pile. Il y a entièrement 21 code de déroulement. Chaque code de déroulement mappe exactement une instruction dans le prologue/épilogue afin de permettre le déroulement des projournaux et épilogues partiellement exécutés.

|Code de déroulement|Bits et interprétation|
|-|-|
|`alloc_s`|000xxxxx : allouez une petite pile de taille \< 512 (2 ^ 5 * 16).|
|`save_r19r20_x`|    001zzzzz : Save \<x19, X20 > paire à [SP-#Z * 8] !, offset pré-indexé > =-248 |
|`save_fplr`|        01zzzzzz : Save \<x29, LR > pair à [SP + #Z * 8], offset \< = 504. |
|`save_fplr_x`|        10zzzzzz : Save \<x29, LR > pair à [SP-(#Z + 1) * 8] !, décalage pré-indexé > =-512 |
|`alloc_m`|        11000xxx’xxxxxxxx : allouez une grande pile de taille \< 16 Ko (2 ^ 11 * 16). |
|`save_regp`|        110010xx’xxzzzzzz : enregistrer la paire x (19 + #X) à [SP + #Z * 8], décalage \< = 504 |
|`save_regp_x`|        110011xx’xxzzzzzz : enregistrer la paire x (19 + #X) à [SP-(#Z + 1) * 8] !, décalage pré-indexé > =-512 |
|`save_reg`|        110100xx’xxzzzzzz : enregistrer reg x (19 + #X) à [SP + #Z * 8], décalage \< = 504 |
|`save_reg_x`|        1101010x’xxxzzzzz : enregistrer reg x (19 + #X) à [SP-(#Z + 1) * 8] !, décalage pré-indexé > =-256 |
|`save_lrpair`|         1101011x’xxzzzzzz : Save pair \<x (19 + 2 *#X), lr > à [SP + #Z*8], offset \< = 504 |
|`save_fregp`|        1101100x’xxzzzzzz : Save pair d (8 + #X) à [SP + #Z * 8], décalage \< = 504 |
|`save_fregp_x`|        1101101x’xxzzzzzz : enregistrer la paire d (8 + #X), à [SP-(#Z + 1) * 8] !, décalage pré-indexé > =-512 |
|`save_freg`|        1101110x’xxzzzzzz : enregistrer reg d (8 + #X) à [SP + #Z * 8], décalage \< = 504 |
|`save_freg_x`|        11011110 'xxxzzzzz : Save reg d (8 + #X) à [SP-(#Z + 1) * 8] !, décalage pré-indexé > =-256 |
|`alloc_l`|         11100000 'xxxxxxxx’xxxxxxxx’xxxxxxxx : allouer une grande pile avec une taille \< 256M (2 ^ 24 * 16) |
|`set_fp`|        11100001 : configurer x29 : avec : MOV x29, SP |
|`add_fp`|        11100010 'xxxxxxxx : configurer x29 avec : Add x29, SP, #x * 8 |
|`nop`|            11100011 : aucune opération de déroulage n’est requise. |
|`end`|            11100100 : fin du code de déroulement. Implique RET dans épilogue. |
|`end_c`|        11100101 : fin du code de déroulement dans la portée chaînée actuelle. |
|`save_next`|        11100110 : enregistrez la paire de registres int ou FP non volatile suivante. |
|`arithmetic(add)`|    11100111 ' 000zxxxx : ajoutez le cookie reg (z) à LR (0 = x28, 1 = SP); Add LR, LR, Reg (z) |
|`arithmetic(sub)`|    11100111 ' 001zxxxx : Sub cookie reg (z) from LR (0 = x28, 1 = SP); Sub LR, LR, Reg (z) |
|`arithmetic(eor)`|    11100111 ' 010zxxxx : EOR LR avec le cookie reg (z) (0 = x28, 1 = SP); EOR LR, LR, Reg (z) |
|`arithmetic(rol)`|    11100111 ' 0110xxxx : ROL simulé de LR avec le cookie reg (x28); xip0 = nég x28 ; ROR LR, xip0 |
|`arithmetic(ror)`|    11100111 ' 100zxxxx : ROR LR avec le cookie reg (z) (0 = x28, 1 = SP); ROR LR, LR, Reg (z) |
| |            11100111 : XXXZ---- :----réservé |
| |              11101xxx : réservé pour les cas de pile personnalisés ci-dessous uniquement générés pour les routines ASM |
| |              11101000 : Pile personnalisée pour MSFT_OP_TRAP_FRAME |
| |              11101001 : Pile personnalisée pour MSFT_OP_MACHINE_FRAME |
| |              11101010 : Pile personnalisée pour MSFT_OP_CONTEXT |
| |              11101100 : Pile personnalisée pour MSFT_OP_CLEAR_UNWOUND_TO_CALL |
| |              1111xxxx : réservé |

Dans les instructions avec des valeurs importantes couvrant plusieurs octets, les bits les plus significatifs sont stockés en premier. Les codes de déroulement ci-dessus sont conçus de telle sorte qu’en recherchant simplement le premier octet du code, il est possible de connaître la taille totale en octets du code de déroulement. Étant donné que chaque code de déroulement est mappé exactement à une instruction dans prologue/épilogue, pour calculer la taille du prologue ou de l’épilogue, il est nécessaire de passer du début de la séquence à la fin, à l’aide d’une table de recherche ou d’un appareil similaire pour déterminer la durée du cor l’opcode de réponse est.

Notez que l’adressage de décalage après indexation n’est pas autorisé dans le prologue. Toutes les plages de décalage (#Z) correspondent à l’encodage de l’adressage STP/STR, à l’exception de `save_r19r20_x`, dans lequel 248 est suffisant pour toutes les zones d’enregistrement (10 registres int + 8 registres FP + 8 registres d’entrée).

`save_next` doit suivre un enregistrement pour la paire de registres volatiles int ou FP : `save_regp`, `save_regp_x`, `save_fregp`, `save_fregp_x`, `save_r19r20_x` ou un autre `save_next`. Elle enregistre la paire de registres suivante à l’emplacement suivant de 16 octets dans l’ordre croissant. `save-next` suivant une `save_next` qui indique que la dernière paire de registres int fait référence à la première paire de registres FP.

Étant donné que la taille des instructions de retour et de saut standard est la même, il n’est pas nécessaire de disposer d’un code de déroulement `end` séparé pour les scénarios d’appel tail.

`end_c` est conçu pour gérer des fragments de fonction non contigus à des fins d’optimisation. @No__t-0 qui indique que la fin des codes de déroulement dans l’étendue actuelle doit être suivie par une autre série de code de déroulement se terminant par un réel `end`. Les codes de déroulement entre `end_c` et `end` représentent les opérations de prologue dans la région parente (Prologue « fantôme »).  Pour plus d’informations et d’exemples, voir la section ci-dessous.

### <a name="packed-unwind-data"></a>Données de déroulement compressées

Pour les fonctions dont les proépiloguess et les suivent la forme canonique décrite ci-dessous, les données de déroulement compressées peuvent être utilisées, éliminant la nécessité d’un enregistrement. XData entièrement et réduisant de manière significative le coût de la fourniture des données de déroulement. Les projournaux et épilogues canoniques sont conçus pour répondre aux exigences courantes d’une fonction simple qui ne nécessite pas de gestionnaire d’exceptions et qui effectue ses opérations d’installation et de destruction dans un ordre standard.

Le format d’un enregistrement. pdata avec des données de déroulement compressées ressemble à ceci :

![enregistrement. pdata avec les données de déroulement compressées](media/arm64-exception-handling-packed-unwind-data.png "enregistrement. pdata avec les données de déroulement compressées")

Les champs sont les suivants :

- **RVA Start Function** est l’adresse RVA 32 bits du début de la fonction.
- L' **indicateur** est un champ de 2 bits comme décrit ci-dessus, avec les significations suivantes :
  - 00 = données de déroulement compressées non utilisées ; points de bits restants vers un enregistrement. XData
  - 01 = données de déroulement compressées utilisées comme décrit ci-dessous avec un prologue et un épilogue uniques au début et à la fin de l’étendue
  - 10 = données de déroulement compressées utilisées comme décrit ci-dessous pour le code sans prologue et épilogue ; Cela est utile pour décrire des segments de fonction séparés.
  - 11 = réservée ;
- La **longueur de fonction** est un champ de 11 bits qui fournit la longueur de la fonction entière en octets, divisée par 4. Si la taille de la fonction est supérieure à 8 Ko, un enregistrement complet. XData doit être utilisé à la place.
- La **taille de frame** est un champ de 9 bits indiquant le nombre d’octets de la pile alloués pour cette fonction, divisé par 16. Les fonctions qui allouent plus de (8 Ko-16) octets de pile doivent utiliser un enregistrement. XData complet. Cela comprend la zone de variables locales, la zone de paramètres sortants, l’appelé, la zone int et FP enregistrée et la zone de paramètres de démarrage, mais à l’exception de la zone d’allocation dynamique.
- **CR** est un indicateur de 2 bits indiquant si la fonction comprend des instructions supplémentaires pour configurer une chaîne de frames et un lien de retour :
  - 00 = fonction non chaînée, \<x29, LR > paire n’est pas enregistrée dans la pile.
  - 01 = fonction non chaînée, \<lr > est enregistrée dans la pile
  - 10 = réservée ;
  - 11 = fonction chaînée, une instruction de paire magasin/chargement est utilisée dans le prologue/épilogue \<x29, LR >
- **H** est un indicateur de 1 bit qui indique si la fonction maison les registres de paramètres entiers (x0-x 7) en les stockant au début de la fonction. (0 = pas de registres personnels, 1 = maisons inscrites).
- **Gion** est un champ de 4 bits indiquant le nombre de registres int non volatiles (x19-x28) enregistrés à l’emplacement de pile canonique.
- **RegF** est un champ de 3 bits indiquant le nombre de registres FP non volatils (D8-D15) enregistrés à l’emplacement de pile canonique. (RegF = 0 : aucun registre FP n’est enregistré ; RegF > 0 : RegF + 1 les registres FP sont enregistrés). Les données de déroulement compressées ne peuvent pas être utilisées pour une fonction qui enregistre un seul registre FP.

Les projournaux canoniques qui appartiennent à des catégories 1, 2 (sans zone de paramètres sortants), 3 et 4 dans la section ci-dessus peuvent être représentés par un format de déroulement compressé.  Les épilogues pour les fonctions canoniques suivent un formulaire très similaire, sauf que **H** n’a aucun effet, que l’instruction `set_fp` est omise et que l’ordre des étapes, ainsi que les instructions de chaque étape, sont inversés dans l’épilogue. L’algorithme des XData compressés suit ces étapes, détaillées dans le tableau suivant :

Étape 0 : Effectuez le précalcul de la taille de chaque zone.

Étape 1 : Enregistrer un appelé int-registres enregistrés.

Étape 2 : Cette étape est spécifique au type 4 dans les premières sections. LR est enregistré à la fin de la zone int.

Étape 3 : Enregistrer l’appelé FP-registres enregistrés.

Étape 4 : Enregistrez les arguments d’entrée dans la zone de paramètres de démarrage.

Étape 5 : Allouez la pile restante, y compris la zone locale, la paire @no__t 0x29, LR > et la zone de paramètres sortants. 5a correspond au type canonique 1. 5b et 5c sont pour le type canonique 2. 5J et 5e sont pour les types 3 et 4.

Première #|Valeurs d’indicateur|nombre d’instructions|Opcode|Code de déroulement
-|-|-|-|-
0|||`#intsz = RegI * 8;`<br/>`if (CR==01) #intsz += 8; // lr`<br/>`#fpsz = RegF * 8;`<br/>`if(RegF) #fpsz += 8;`<br/>`#savsz=((#intsz+#fpsz+8*8*H)+0xf)&~0xf)`<br/>`#locsz = #famsz - #savsz`|
1|0 < **gion** < = 10|Gion/2 + **gion** % 2|`stp x19,x20,[sp,#savsz]!`<br/>`stp x21,x22,[sp,#16]`<br/>`...`|`save_regp_x`<br/>`save_regp`<br/>`...`
2|**CR**==01*|1|`str lr,[sp,#(intsz-8)]`\*|`save_reg`
3|0 < **RegF** < = 7|(RegF + 1)/2 +<br/>(RegF + 1)% 2)|`stp d8,d9,[sp,#intsz]`\*\*<br/>`stp d10,d11,[sp,#(intsz+16)]`<br/>`...`<br/>`str d(8+RegF),[sp,#(intsz+fpsz-8)]`|`save_fregp`<br/>`...`<br/>`save_freg`
4|**H** == 1|4|`stp x0,x1,[sp,#(intsz+fpsz)]`<br/>`stp x2,x3,[sp,#(intsz+fpsz+16)]`<br/>`stp x4,x5,[sp,#(intsz+fpsz+32)]`<br/>`stp x6,x7,[sp,#(intsz+fpsz+48)]`|`nop`<br/>`nop`<br/>`nop`<br/>`nop`
5a|**CR** == 11 && #locsz<br/> <= 512|2|`stp x29,lr,[sp,#-locsz]!`<br/>`mov x29,sp`\*\*\*|`save_fplr_x`<br/>`set_fp`
5b|**CR** == 11 &&<br/>512 < #locsz <= 4080|3|`sub sp,sp,#locsz`<br/>`stp x29,lr,[sp,0]`<br/>`add x29,sp,0`|`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5C|**CR** == 11 && #locsz > 4080|4|`sub sp,sp,4080`<br/>`sub sp,sp,#(locsz-4080)`<br/>`stp x29,lr,[sp,0]`<br/>`add x29,sp,0`|`alloc_m`<br/>`alloc_s`/`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5D|(**CR** == 00 \|\| **CR**==01) &&<br/>#locsz <= 4080|1|`sub sp,sp,#locsz`|`alloc_s`/`alloc_m`
5e|(**CR** == 00 \|\| **CR**==01) &&<br/>#locsz > 4080|2|`sub sp,sp,4080`<br/>`sub sp,sp,#(locsz-4080)`|`alloc_m`<br/>`alloc_s`/`alloc_m`

\* si **CR** = = 01 et **gion** est un nombre impair, l’étape 2 et la dernière save_rep de l’étape 1 sont fusionnées dans un save_regp.

\* @ no__t-1 si **gion** == **CR** = = 0 et **RegF** ! = 0, le premier STP pour la virgule flottante effectue le prédécrémentation.

\* @ no__t-1 @ no__t-2 aucune instruction correspondant à `mov x29,sp` est présente dans l’épilogue. Les données de déroulement compressées ne peuvent pas être utilisées si une fonction requiert la restauration du SP à partir de x29.

### <a name="unwinding-partial-prologs-and-epilogs"></a>Déroulement partiel des projournalions et des épilogues

La situation de déroulement le plus courant est celle dans laquelle l’exception ou l’appel s’est produit dans le corps de la fonction, en dehors du prologue et de tous les épilogues. Dans ce cas, le déroulement est simple : le dérouleur commence simplement à exécuter les codes dans le tableau de déroulement en commençant à l’index 0 et en continuant jusqu’à ce qu’un opcode de fin soit détecté.

Il est plus difficile de le dérouler correctement dans le cas où une exception ou une interruption se produit lors de l’exécution d’un prologue ou d’un épilogue. Dans ces situations, le frame de pile n’est que partiellement construit, et l’astuce consiste à déterminer exactement ce qui a été fait pour l’annuler correctement.

Par exemple, prenez ce prologue et la séquence d’épilogue :

```asm
0000:    stp    x29,lr,[sp,#-256]!          // save_fplr_x  256 (pre-indexed store)
0004:    stp    d8,d9,[sp,#224]             // save_fregp 0, 224
0008:    stp    x19,x20,[sp,#240]           // save_regp 0, 240
000c:    mov    x29,sp                      // set_fp
         ...
0100:    mov    sp,x29                      // set_fp
0104:    ldp    x19,x20,[sp,#240]           // save_regp 0, 240
0108:    ldp    d8,d9,[sp,224]              // save_fregp 0, 224
010c:    ldp    x29,lr,[sp],#256            // save_fplr_x  256 (post-indexed load)
0110:    ret    lr                          // end
```

En regard de chaque opcode se trouve le code de déroulement approprié qui décrit cette opération. La première chose à noter est que la série de codes de déroulement du prologue est une image miroir exacte des codes de déroulement pour l’épilogue (sans compter l’instruction finale de l’épilogue). Il s’agit d’une situation courante et, pour cette raison, les codes de déroulement du prologue sont toujours supposés être stockés dans l’ordre inverse à partir de l’ordre d’exécution du prologue.

Ainsi, pour le prologue et l’épilogue, nous avons laissé un ensemble commun de codes de déroulement :

`set_fp`, `save_regp 0,240`, `save_fregp,0,224`, `save_fplr_x_256`, `end`

En commençant par le cas d’épilogue (plus simple, comme dans l’ordre normal), à l’offset 0 dans l’épilogue (qui commence à l’offset 0x100 dans la fonction), nous attendions l’exécution de la séquence de déroulement complète, car aucun nettoyage n’a encore été effectué. Si nous nous trouvons une instruction dans (au décalage 2 dans l’épilogue), nous pouvons effectuer une déroulation en ignorant le premier code de déroulement. Pour généraliser cette situation, en supposant un mappage de 1:1 entre les OpCodes et les codes de déroulement, nous pouvons indiquer que si nous effectuons le déroulement à partir de l’instruction n dans l’épilogue, nous devrions ignorer les n premiers codes de déroulement et commencer à exécuter à partir de là.

Il s’avère qu’une logique similaire fonctionne pour le prologue, sauf en sens inverse. Si nous déroulons du décalage 0 dans le prologue, nous souhaitons n’exécuter aucune action. Si nous déroulons l’offset 2, qui est une instruction dans, nous souhaitons commencer à exécuter la séquence de déroulement un code de déroulement à partir de la fin (n’oubliez pas que les codes sont stockés dans l’ordre inverse). Nous pouvons également généraliser que si nous déroulons à partir de l’instruction n dans le prologue, nous devons commencer à exécuter n codes de déroulement à partir de la fin de la liste de codes.

À présent, il n’est pas toujours le cas que le prologue et les codes d’épilogue correspondent exactement. Pour cette raison, il se peut que le tableau de déroulement doive contenir plusieurs séquences de codes. Pour déterminer le décalage de l’emplacement où commencer le traitement des codes, utilisez la logique suivante :

1. Si vous effectuez un déroulement à partir du corps de la fonction, commencez simplement à exécuter les codes de déroulement à l’index 0 et continuez jusqu’à ce qu’il atteigne un opcode « end ».

1. En cas de déroulement à partir d’un épilogue, utilisez l’index de départ spécifique à l’épilogu fourni avec la portée d’épilogue comme point de départ. Calculez le nombre d’octets du PC en question à partir du début de l’épilogue. Ensuite, avancez dans les codes de déroulement, en ignorant les codes de déroulement jusqu’à ce que toutes les instructions déjà exécutées soient prises en compte. Exécutez ensuite à partir de ce point.

1. Si vous procédez à un déroulement à partir du prologue, utilisez l’index 0 comme point de départ. Calculez la longueur du code de prologue à partir de la séquence, puis calculez le nombre d’octets du PC en question à partir de la fin du prologue. Ensuite, avancez dans les codes de déroulement, en ignorant les codes de déroulement jusqu’à ce que toutes les instructions qui n’ont pas encore été exécutées soient prises en compte. Exécutez ensuite à partir de ce point.

À la suite de ces règles, les codes de déroulement du prologue doivent toujours être le premier dans le tableau, et ils sont également les codes utilisés pour se dérouler dans le cas général du déroulement à partir du corps. Toutes les séquences de code spécifiques à un épilogue doivent suivre immédiatement après.

### <a name="function-fragments"></a>Fragments de fonction

À des fins d’optimisation du code et pour d’autres raisons, il peut être préférable de fractionner une fonction en fragments séparés (également appelés régions). Lorsque c’est fait, chaque fragment de fonction résultant requiert son propre enregistrement. pdata (et éventuellement. XData).

Dans le cas d’un fragment secondaire séparé ayant son propre prologue, il est prévu qu’aucun ajustement de la pile ne soit effectué dans son prologue. Tout l’espace de pile requis par les régions secondaires doit être pré-alloué par sa région parente (ou région hôte). Cela conserve strictement la manipulation du pointeur de pile dans le prologue d’origine de la fonction.

Un cas typique de fragments de fonction est la « séparation de code » avec ce compilateur qui peut déplacer une région de code hors de sa fonction hôte. Il existe trois cas inhabituels qui peuvent résulter de la séparation de code.

#### <a name="example"></a>Exemple :

- (région 1 : début)

    ```asm
        stp     x29,lr,[sp,#-256]!      // save_fplr_x  256 (pre-indexed store)
        stp     x19,x20,[sp,#240]       // save_regp 0, 240
        mov     x29,sp                  // set_fp
        ...
    ```

- (région 1 : fin)
- (région 3 : début)

    ```asm
        ...
    ```

- (région 3 : fin)
- (région 2 : début)

    ```asm
    ...
        mov     sp,x29                  // set_fp
        ldp     x19,x20,[sp,#240]       // save_regp 0, 240
        ldp     x29,lr,[sp],#256        // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- (région 2 : fin)

1. Prologue uniquement (région 1 : toutes les épilogues se trouvent dans des régions séparées) :

   Seul le prologue doit être décrit. Cela ne peut pas être représenté par le format compact. pData. Dans le cas complet. XData, cette valeur peut être représentée en définissant l’épilogue Count = 0. Consultez la région 1 dans l’exemple ci-dessus.

   Codes de déroulement : `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end`.

1. Épilogues uniquement (région 2 : le prologue est dans la région hôte)

   Il est supposé que, lors du saut de contrôle dans cette région, tous les codes de prologue ont été exécutés. Un déroulement partiel peut se produire dans épilogues de la même façon que dans une fonction normale. Ce type de région ne peut pas être représenté par compact. pData. Dans l’enregistrement de XData complet, il peut être encodé avec un prologue « fantôme », entre une paire de codes de déroulement `end_c` et `end`.  Le @no__t de début-0 indique que la taille du prologue est égale à zéro. L’index de début d’épilogue de l’épilogue unique pointe vers `set_fp`.

   Code de déroulement pour la région 2 : `end_c`, `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end`.

1. Aucun projournal ou épilogues (région 3 : les projournals et tous les épilogues se trouvent dans d’autres fragments) :

   Le format compact. pdata peut être appliqué via l’indicateur de paramètre = 10. Avec l’enregistrement Full. XData, épilogue Count = 1. Le code de déroulement est le même que celui de la région 2 ci-dessus, mais l’index de début d’épilogue pointe également vers `end_c`. Le déroulement partiel ne se produira jamais dans cette région de code.

Un autre cas plus compliqué de fragments de fonction consiste à « réduire l’habillage » avec ce compilateur peut choisir de différer l’enregistrement de certains registres enregistrés, jusqu’à l’extérieur du prologue d’entrée de fonction.

- (région 1 : début)

    ```asm
        stp     x29,lr,[sp,#-256]!      // save_fplr_x  256 (pre-indexed store)
        stp     x19,x20,[sp,#240]       // save_regp 0, 240
        mov     x29,sp                  // set_fp
        ...
    ```

- (région 2 : début)

    ```asm
        stp     x21,x22,[sp,#224]       // save_regp 2, 224
        ...
        ldp     x21,x22,[sp,#224]       // save_regp 2, 224
    ```

- (région 2 : fin)

    ```asm
        ...
        mov     sp,x29                  // set_fp
        ldp     x19,x20,[sp,#240]       // save_regp 0, 240
        ldp     x29,lr,[sp],#256        // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- (région 1 : fin)

Dans le prologue de la région 1, l’espace de pile est pré-alloué. Notez que la région 2 aura le même code de déroulement, même si elle est déplacée hors de sa fonction hôte.

Région 1 : `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end` avec l’index de début d’épilogue pointe vers `set_fp` comme d’habitude.

Région 2 : `save_regp 2, 224`, `end_c`, `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end`. L’index de début d’épilogue pointe vers le premier code de déroulement `save_regp 2, 224`.

### <a name="large-functions"></a>Fonctions volumineuses

Les fragments peuvent être utilisés pour décrire des fonctions supérieures à la limite de 1 million imposée par les champs de bits dans l’en-tête. XData. Pour décrire une fonction très volumineuse comme celle-ci, elle doit simplement être divisée en fragments inférieurs à 1M. Chaque fragment doit être ajusté pour ne pas fractionner un épilogu en plusieurs parties.

Seul le premier fragment de la fonction contiendra un prologue ; tous les autres fragments sont marqués comme n’ayant aucun prologue. Selon le nombre de épilogues présents, chaque fragment peut contenir zéro ou plusieurs épilogues. Gardez à l’esprit que chaque portée d’épilogue dans un fragment spécifie son décalage de départ par rapport au début du fragment, et non le début de la fonction.

Si un fragment n’a pas de prologue ni d’épilogue, il requiert toujours son propre enregistrement. pdata (et éventuellement. XData) pour décrire comment se dérouler dans le corps de la fonction.

## <a name="examples"></a>Exemples

### <a name="example-1-frame-chained-compact-form"></a>Exemple 1 : Image chaînée, compact-Form

```asm
|Foo|     PROC
|$LN19|
    str     x19,[sp,#-0x10]!        // save_reg_x
    sub     sp,sp,#0x810            // alloc_m
    stp     fp,lr,[sp]              // save_fplr
    mov     fp,sp                   // set_fp
                                    //  end of prolog
    ...

|$pdata$Foo|
    DCD     imagerel     |$LN19|
    DCD     0x416101ed
    ;Flags[SingleProEpi] functionLength[492] RegF[0] RegI[1] H[0] frameChainReturn[Chained] frameSize[2080]
```

### <a name="example-2-frame-chained-full-form-with-mirror-prolog--epilog"></a>Exemple 2 : Mise en miroir de la trame, pleine forme avec mise en miroir & épilogue

```asm
|Bar|     PROC
|$LN19|
    stp     x19,x20,[sp,#-0x10]!    // save_regp_x
    stp     fp,lr,[sp,#-0x90]!      // save_fplr_x
    mov     fp,sp                   // set_fp
                                    // end of prolog
    ...
                                    // begin of epilog, a mirror sequence of Prolog
    mov     sp,fp
    ldp     fp,lr,[sp],#0x90
    ldp     x19,x20,[sp],#0x10
    ret     lr

|$pdata$Bar|
    DCD     imagerel     |$LN19|
    DCD     imagerel     |$unwind$cse2|
|$unwind$Bar|
    DCD     0x1040003d
    DCD     0x1000038
    DCD     0xe42291e1
    DCD     0xe42291e1
    ;Code Words[2], Epilog Count[1], E[0], X[0], Function Length[6660]
    ;Epilog Start Index[0], Epilog Start Offset[56]
    ;set_fp
    ;save_fplr_x
    ;save_r19r20_x
    ;end
```

Notez que l’index EpilogStart [0] pointe vers la même séquence de code de déroulement de prologue.

### <a name="example-3-variadic-unchained-function"></a>Exemple 3 : Variadiques fonction déchaînée

```asm
|Delegate| PROC
|$LN4|
    sub     sp,sp,#0x50
    stp     x19,lr,[sp]
    stp     x0,x1,[sp,#0x10]        // save incoming register to home area
    stp     x2,x3,[sp,#0x20]        // ...
    stp     x4,x5,[sp,#0x30]
    stp     x6,x7,[sp,#0x40]        // end of prolog
    ...
    ldp     x19,lr,[sp]             // beginning of epilog
    add     sp,sp,#0x50
    ret     lr

    AREA    |.pdata|, PDATA
|$pdata$Delegate|
    DCD     imagerel |$LN4|
    DCD     imagerel |$unwind$Delegate|

    AREA    |.xdata|, DATA
|$unwind$Delegate|
    DCD     0x18400012
    DCD     0x200000f
    DCD     0xe3e3e3e3
    DCD     0xe40500d6
    DCD     0xe40500d6
    ;Code Words[3], Epilog Count[1], E[0], X[0], Function Length[18]
    ;Epilog Start Index[4], Epilog Start Offset[15]
    ;nop        // nop for saving in home area
    ;nop        // ditto
    ;nop        // ditto
    ;nop        // ditto
    ;save_lrpair
    ;alloc_s
    ;end
```

Remarque : L’index EpilogStart [4] pointe vers le milieu du code de déroulement du Prologue (réutilisation partielle du tableau de déroulement).

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble des conventions ABI ARM64](arm64-windows-abi-conventions.md)<br/>
[Gestion des exceptions ARM](arm-exception-handling.md)
