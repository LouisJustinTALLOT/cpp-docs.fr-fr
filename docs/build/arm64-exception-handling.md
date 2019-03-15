---
title: La gestion des exceptions ARM64
ms.date: 11/19/2018
ms.openlocfilehash: 921029704e4bf5adabfbe0a82387dadc911b9036
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816150"
---
# <a name="arm64-exception-handling"></a>La gestion des exceptions ARM64

Windows sur ARM64 utilise la même gestion structurée des exceptions mécanisme pour asynchrones exceptions générées par le matériel et des exceptions synchrones générées par les logiciels. Les gestionnaires d'exceptions propres aux langages s'appuient sur la gestion des exceptions structurées Windows en utilisant des fonctions d'assistance de langage. Ce document décrit la gestion des exceptions dans Windows sur ARM64 et les programmes d’assistance de langage utilisés par le code généré par l’assembleur Microsoft ARM et le compilateur MSVC.

## <a name="goals-and-motivation"></a>Objectifs et motivation

Les conventions de données de déroulement exception et cette description, sont destinés à :

1. Fournissez suffisamment description pour permettre le déroulement sans code dans tous les cas de détection.

   - L’analyse du code requiert que le code soit paginée à. Cela empêche le déroulement dans certaines circonstances, il est utile (le suivi, d’échantillonnage, le débogage).

   - L’analyse du code est complexe ; le compilateur doit être prudent générer uniquement des instructions que le dérouleur est capable de décoder.

   - Si le déroulement ne peut pas être décrit en détail grâce à l’utilisation de codes de déroulement, puis dans certains cas il doit revenir à décodage de l’instruction. Cela accroît la complexité globale et dans l’idéal, cela permet d’éviter.

1. Prise en charge déroulement dans le milieu de prologue et épilogue intermédiaire.

   - Le déroulement est utilisé dans Windows depuis plus de la gestion des exceptions, il est donc essentiel que nous être en mesure d’effectuer une liste précise déroulement même quand au milieu d’une séquence de code de prologue ni d’épilogue.

1. Prendre une quantité minimale d’espace.

   - Les codes de déroulement ne doivent pas agréger pour augmenter considérablement la taille du binaire.

   - Étant donné que les codes de déroulement sont susceptibles d’être verrouillé en mémoire, un faible encombrement mémoire garantit une surcharge minimale pour chaque fichier binaire chargé.

## <a name="assumptions"></a>Assumptions (Hypothèses)

Il s’agit de la description des exceptions hypothèses :

1. Les prologues et épilogues ont tendance à mettre en miroir de deux autres. En tirant parti de cette caractéristique commune, la taille des métadonnées nécessaires pour décrire le déroulement peut être considérablement réduite. Dans le corps de la fonction, peu importe si les opérations du prologue sont annulées ou les opérations de l’épilogue sont effectuées à l’avance. Les deux doivent produire des résultats identiques.

1. Les fonctions sont généralement dans l’ensemble relativement faible. Plusieurs optimisations pour espace s’appuient sur ce afin d’optimiser la compression la plus efficace de données.

1. Il n’y a aucun code conditionnel dans épilogues.

1. Registre de pointeur de frame dédié : Si la procédure stockée est enregistrée dans un autre registre (r29) dans le prologue, ce qui s’inscrivent reste inchangée tout au long de la fonction, afin que le sp d’origine peut être libéré à tout moment.

1. À moins que le sp soit enregistré dans un autre registre, toutes les manipulations dont le pointeur de pile se produit strictement dans le prologue et épilogue.

1. La disposition du frame de pile est organisée comme décrit dans la section suivante.

## <a name="arm64-stack-frame-layout"></a>Disposition du frame de pile ARM64

![disposition du frame de pile](media/arm64-exception-handling-stack-frame.png "disposition du frame de pile")

Pour les fonctions de frame chaînée, la paire fp et lr peut être enregistrée à n’importe quelle position dans la zone de variable locale en fonction des considérations d’optimisation. L’objectif est de maximiser le nombre de variables locales qui peut être atteint par une instruction unique basée sur le pointeur de frame (r29) ou le pointeur de pile (sp). Toutefois pour `alloca` fonctions, il doit être chaîné et r29 doit pointer vers le bas de pile. Pour permettre une meilleure couverture register-paire-adressage-mode, non volatile inscrire aave zones sont positionnés en haut de la pile de réseau Local. Voici des exemples qui illustrent certains des séquences de prologue plus efficaces. Par souci de clarté une meilleure localité de cache, l’ordre de stockage de registres enregistrés des appelés dans tous les prologues canoniques est dans l’ordre « croissante des ». `#framesz` ci-dessous représente la taille de pile entière (à l’exclusion de la zone d’alloca). `#localsz` et `#outsz` indiquent la taille de la zone locale (y compris l’enregistrement concernant la \<r29, lr > paire) et sortant de taille de paramètre, respectivement.

1. Chained, #localsz \<= 512

    ```asm
        stp    r19,r20,[sp,-96]!        // pre-indexed, save in 1st FP/INT pair
        stp    d8,d9,[sp,16]            // save in FP regs (optional)
        stp    r0,r1,[sp,32]            // home params (optional)
        stp    r2,r3,[sp, 48]
        stp    r4,r5,[sp,64]
        stp    r6,r7,[sp,72]
        stp    r29, lr, [sp, -#localsz]!    // save <r29,lr> at bottom of local area
        mov    r29,sp                   // r29 points to bottom of local
        sub    sp, #outsz               // (optional for #outsz != 0)
    ```

1. Chained, #localsz > 512

    ```asm
        stp    r19,r20,[sp,-96]!        // pre-indexed, save in 1st FP/INT pair
        stp    d8,d9,[sp,16]            // save in FP regs (optional)
        stp    r0,r1,[sp,32]            // home params (optional)
        stp    r2,r3,[sp, 48]
        stp    r4,r5,[sp,64]
        stp    r6,r7,[sp,72]
        sub    sp,#localsz+#outsz       // allocate remaining frame
        stp    r29, lr, [sp, #outsz]    // save <r29,lr> at bottom of local area
        add    r29,sp, #outsz           // setup r29 points to bottom of local area
    ```

1. Fonctions de feuille non chaîné, (lr ne sont pas enregistré)

    ```asm
        stp    r19,r20,[sp, -72]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    r21,r22,[sp, 16]
        str    r23 [sp,32]
        stp    d8,d9,[sp,40]            // save FP regs (optional)
        stp    d10,d11,[sp,56]
        sub    sp,#framesz-72           // allocate the remaining local area
    ```

   Toutes les variables locales sont accessibles selon le fournisseur de services. \<R29, lr > pointe vers le frame précédent. Pour la taille de trame \<= 512, la « sub sp,... » peuvent être optimisées, si la zone de réglementations enregistrées est déplacée vers le bas de la pile. L’inconvénient de qui est qu’il n’est pas cohérente avec les autres dispositions ci-dessus et réglementations enregistrées tirer partie de la plage pour le respect de la paire et mode d’adressage de décalage pré- et post-indexé.

1. Fonctions non chaînées, non terminaux (lr est enregistrée dans la zone de Int enregistré)

    ```asm
        stp    r19,r20,[sp,-80]!        // pre-indexed, save in 1st FP/INT reg-pair
        stp    r21,r22,[sp,16]          // ...
        stp    r23, lr,[sp, 32]         // save last Int reg and lr
        stp    d8,d9,[sp, 48]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,64]          // ...
        sub    sp,#framesz-80           // allocate the remaining local area
    ```

   Ou, avec un nombre pair enregistré Int registres,

    ```asm
        stp    r19,r20,[sp,-72]!        // pre-indexed, save in 1st FP/INT reg-pair
        stp    r21,r22,[sp,16]          // ...
        str    lr,[sp, 32]              // save lr
        stp    d8,d9,[sp, 40]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,56]          // ...
        sub    sp,#framesz-72           // allocate the remaining local area
    ```

   R19 uniquement enregistré :

    ```asm
        sub    sp, sp, #16              // reg save area allocation*
        stp    r19,lr,[sp,0]            // save r19, lr
        sub    sp,#framesz-16           // allocate the remaining local area
    ```

   \* Le reg enregistrer l’allocation de la zone n’est pas assemblée dans le protocole stp, car un stp reg-lr préalable indexée ne peut pas être représentée avec les codes de déroulement.

   Toutes les variables locales sont accessibles selon le fournisseur de services. \<R29 > pointe vers le frame précédent.

1. Chained, #framesz \<= 512, #outsz = 0

    ```asm
        stp    r29, lr, [sp, -#framesz]!    // pre-indexed, save <r29,lr>
        mov    r29,sp                       // r29 points to bottom of stack
        stp    r19,r20,[sp, #framesz -32]   // save INT pair
        stp    d8,d9,[sp, #framesz -16]     // save FP pair
    ```

   Comparaison de prologue #1 ci-dessus, l’avantage est que register toutes les instructions d’enregistrement sont prêtes à être exécutées immédiatement après la pile qu’une seule allocation d’instruction. Ainsi, il n’existe aucune dépendance anti-vis-à-vis des SP qui empêche le parallélisme au niveau instruction.

1. Taille d’image chaînées, 512 > (facultatif pour les fonctions sans alloca)

    ```asm
        stp    r29, lr, [sp, -80]!          // pre-indexed, save <r29,lr>
        stp    r19,r20,[sp,16]              // save in INT regs
        stp    r21,r22,[sp,32]              // ...
        stp    d8,d9,[sp,48]                // save in FP regs
        stp    d10,d11,[sp,64]
        mov    r29,sp                       // r29 points to top of local area
        sub    sp,#framesz-80               // allocate the remaining local area
    ```

   À des fins d’optimisation, r29 peuvent être placés à n’importe quelle position dans la zone locale pour offrir une meilleure couverture « reg-paire » et pré/post indexed décalage mode d’adressage. Variables locales ci-dessous des pointeurs de frame sont accessibles selon le fournisseur de services.

1. Taille d’image chaînées, > 4K, avec ou sans alloca(),

    ```asm
        stp    r29, lr, [sp, -80]!          // pre-indexed, save <r29,lr>
        stp    r19,r20,[sp,16]              // save in INT regs
        stp    r21,r22,[sp,32]              // ...
        stp    d8,d9,[sp,48]                // save in FP regs
        stp    d10,d11,[sp,64]
        mov    r29,sp                       // r29 points to top of local area
        mov    r8, #framesz/16
        bl     chkstk
        sub    sp, r8*16                    // allocate remaining frame
                                            // end of prolog
        ...
        sp = alloca                         // more alloca() in body
        ...
                                            // beginning of epilog
        mov    sp,r29                       // sp points to top of local area
        ldp    d10,d11, [sp,64],
        ...
        ldp    r29, lr, [sp], -80           // post-indexed, reload <r29,lr>
    ```

## <a name="arm64-exception-handling-information"></a>Informations de gestion d’exception ARM64

### <a name="pdata-records"></a>enregistrements .pdata

Les enregistrements .pdata sont un tableau ordonné d’éléments de longueur fixe qui décrivent chaque fonction de manipulation de pile dans un fichier binaire PE. Notez soigneusement la phrase « manipulation de pile » : les fonctions de feuille qui ne nécessitent pas de n’importe quel stockage local et qui n’ont pas besoin enregistrer/restaurer des registres non volatils ne nécessitent pas un enregistrement .pdata. Il doivent être explicitement omis pour économiser de l’espace. Un déroulement à partir d’une de ces fonctions peut simplement obtenir l’adresse de retour LR à déplacer vers le haut à l’appelant.

Chaque enregistrement .pdata pour ARM64 est la longueur de 8 octets. Le format général des chaque enregistrement endroits l’adresse RVA 32 bits de la fonction Démarrer dans le premier mot, suivi d’une seconde comportant qui contient un pointeur vers un bloc .xdata de longueur variable, ou un mot compressé qui décrit une séquence de déroulement canonique.

![disposition des enregistrements .pdata](media/arm64-exception-handling-pdata-record.png "disposition des enregistrements .pdata")

Les champs sont les suivantes :

- **Fonction RVA Démarrer** est l’adresse RVA 32 bits du début de la fonction.

- **Indicateur** est un champ de 2 bits qui indique comment interpréter les 30 bits restants du deuxième mot .pdata. Si **indicateur** est égal à 0, puis les bits restants forment un **Exception informations RVA** (avec les deux bits inférieurs ayant implicitement la valeur 0). Si **indicateur** est différente de zéro, puis les bits restants forment un **données de déroulement compressées** structure.

- **Exception informations RVA** est l’adresse de la structure d’informations d’exceptions de longueur variable stockée dans la section .xdata. Ces données doivent être alignées sur 4 octets.

- **Compressé des données de déroulement** est une description compressée des opérations nécessaires au déroulement à partir d’une fonction, en supposant que la forme canonique. Dans ce cas, aucun enregistrement .xdata n'est nécessaire.

### <a name="xdata-records"></a>enregistrements .xdata

Quand le format de déroulement compressé ne suffit pas à décrire le déroulement d'une fonction, un enregistrement .xdata de longueur variable doit être créé. L'adresse de cet enregistrement est stockée dans le deuxième mot de l'enregistrement .pdata. Le format de l’enregistrement .xdata est un ensemble de longueur variable compressé de mots :

![disposition d’enregistrement .xdata](media/arm64-exception-handling-xdata-record.png "disposition des enregistrements .xdata")

Ces données sont divisées en quatre sections :

1. Un en-tête 1 ou 2 mots décrivant la taille globale de la structure et de fournir des données de la clé de fonction. Le deuxième mot est présent uniquement si les deux le **épilogue nombre** et **Code mots** champs sont définis sur 0. Voici les champs de bits dans l’en-tête :

   a. **Longueur de la fonction** est un champ de 18 bits qui indique la longueur totale de la fonction en octets, divisé par 4. Si une fonction est supérieure à 1 million, plusieurs enregistrements pdata et xdata doivent être utilisés pour décrire la fonction. Consultez le [les fonctions volumineuses](#large-functions) section pour plus d’informations.

   b. **Vers** est un champ de 2 bits qui décrit la version de l’enregistrement xdata restant. À ce jour, seule la version 0 est définie, et par conséquent, les valeurs de 1 à 3 ne sont pas autorisées.

   c. **X** est un champ de 1 bit qui indique la présence (1) ou non (0) des données d’exception.

   d. **E** est un champ de bits indique que les informations décrivant un épilogue unique est compressé dans l’en-tête (1) au lieu de demander l’étendue supplémentaire mots ultérieures (0).

   e. **Nombre d’épilogue** est un champ de 5 bits qui a deux significations, selon l’état de **E** bits :

      1. Si **E** est définie sur 0 : elle spécifie le nombre du nombre total d’étendues d’exception décrites dans la section 2. Si plus de 31 portées existent dans la fonction, puis le **Code mots** champ doit être défini sur 0 pour indiquer qu’un mot d’extension est nécessaire.

      2. Si **E** est définie sur 1, ce champ spécifie l’index du premier code de déroulement qui décrit l’et épilogue uniquement.

   f. **Les mots de code** est un champ de 5 bits qui spécifie le nombre de mots de 32 bits nécessaires pour contenir tous les codes de déroulement à la section 4. Si plus de 31 mots sont nécessaires (par exemple, plus de 124 dérouler les octets de code), puis ce champ doit être défini sur 0 pour indiquer qu’un mot d’extension est nécessaire.

   g. **Étendue épilogue nombre** et **mots de Code étendu** sont des champs de 16 bits et 8 bits, respectivement, qui fournissent davantage d’espace pour l’encodage d’un nombre anormalement élevé d’épilogues ou un nombre exceptionnellement élevé de mots de code de déroulement. Le mot d’extension qui contient ces champs est présent uniquement si les deux le **épilogue nombre** et **Code mots** champs dans le premier mot d’en-tête sont définies sur 0.

1. Une fois les données d’exception, si **épilogue nombre** n’est pas égal à zéro, est une liste d’informations sur les portées d’épilogue, compressés dans un mot et stockées par ordre croissant de décalage de départ. Chaque portée contient les bits suivants :

   a. **Décalage de début d’épilogue** est un champ de 18 bits qui décrit le décalage en octets, divisé par 4, de l’épilogue par rapport au début de la fonction

   b. **Res** est un champ de 4 bits réservé pour l’extension future. Il doit avoir la valeur 0.

   c. **Index de début d’épilogue** est de 10 bits (plus de 2 bits que **mots de Code étendu**) champ indiquant l’index d’octet du premier code qui décrit cet épilogue de déroulement.

1. Une fois que la liste des portées d’épilogue figure un tableau d’octets qui contient les codes de déroulement, décrits en détail dans une section ultérieure. Ce tableau est rempli à la fin jusqu'à la limite du mot complet le plus proche. Les octets sont stockés dans un ordre Little-Endian, ce qui permet de les récupérer directement en mode Little-Endian.

1. Enfin, après les octets de code de déroulement (et si le **X** bit dans l’en-tête a été défini sur 1) est fourni les informations de gestionnaire d’exception. Il s’agit d’un seul **RVA de gestionnaire d’Exception** en fournissant l’adresse du Gestionnaire d’exceptions lui-même, immédiatement suivi d’une quantité de longueur variable de données requises par le Gestionnaire d’exceptions.

L’enregistrement .xdata ci-dessus est conçu tel qu’il soit possible d’extraire les 8 premiers octets et de celui calculer la taille totale de l’enregistrement (moins la longueur des données d’exception de taille variable qui suit). L’extrait de code suivant calcule la taille d’enregistrement :

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

Il convient de noter que bien que le prologue et chaque épilogue a son propre index dans les codes de déroulement, la table est partagée entre eux, et il est tout à fait possible (et pas complètement rare) qu’ils puissent tous partager les mêmes codes (voir l’exemple 2 dans l’annexe A ci-dessous). Writers de compilateur doivent optimiser dans ce cas, en particulier, car le plus grand index peut être spécifié est de 255, ce qui limite le nombre total de codes de déroulement pour une fonction particulière.

### <a name="unwind-codes"></a>Codes de déroulement

Le tableau de codes de déroulement est un pool de séquences qui indiquent exactement comment annuler les effets du prologue, dans l’ordre dans lequel les opérations doivent être annulées. Les codes de déroulement peuvent être considérés comme un jeu d’instructions mini, encodé sous forme de chaîne d’octets. Lors de l’exécution est terminée, l’adresse de retour à la fonction appelante est dans le Registre lr, et tous les registres non volatils sont restaurés sur leurs valeurs au moment de que la fonction a été appelée.

Si les exceptions ont été garanties ne se produisaient au sein d’un corps de fonction (et jamais avec un prologue ou un épilogue), uniquement une seule séquence serait nécessaire. Toutefois, le modèle de déroulement Windows requiert que nous être en mesure de déroulement à partir un prologue partiellement exécuté ni d’épilogue. Afin de satisfaire cette exigence, les codes de déroulement ont été soigneusement conçus tels qu’ils sont mappés sans ambiguïté 1:1 à chaque opcode approprié dans le prologue et épilogue. Cela a plusieurs conséquences :

1. En comptant le nombre de codes de déroulement, il est possible de calculer la longueur du prologue et épilogue.

1. En comptant le nombre d’instructions après le début d’une portée d’épilogue, il est possible d’ignorer le nombre équivalent de codes de déroulement et d’exécuter le reste d’une séquence pour terminer le partiellement exécuté déroulement de l’exécution de l’épilogue.

1. En comptant le nombre d’instructions avant la fin du prologue, il est possible d’ignorer le nombre équivalent de codes de déroulement et d’exécuter le reste de la séquence à annuler uniquement les parties du prologue qui ont terminé leur exécution.

Les codes de déroulement sont encodées selon le tableau ci-dessous. Tous les codes de déroulement sont un octet unique/double, sauf celui qui alloue une énorme. Voici les totalement 21 code de déroulement. Chaque déroulement code maps exactement une seule instruction dans le prologue/épilogue afin de permettre le déroulement de partiellement exécuté les prologues et épilogues.

|Code de déroulement|Bits et l’interprétation|
|-|-|
|`alloc_s`|000xxxxx : allouer de la petite pile avec taille \< 512 (2 ^ 5 * 16).|
|`save_r19r20_x`|    001zzzzz : enregistrer \<r19, r 20 > la paire à [Z sp-# * 8] !, décalage préalable indexée > =-248 |
|`save_fplr`|        01zzzzzz : enregistrer \<r29, lr > coupler à [sp + #Z * 8], décalage \<= 504. |
|`save_fplr_x`|        10zzzzzz : enregistrer \<r29, lr > coupler à [sp-(#Z + 1) * 8] !, décalage préalable indexée > = -512 |
|`alloc_m`|        11000xxx'xxxxxxxx : allouer de la pile volumineuses avec taille \< 16 k (2 ^ 11 * 16). |
|`save_regp`|        110010xx'xxzzzzzz : enregistrer la paire de r(19+#X) à [sp + #Z * 8], décalage \<= 504 |
|`save_regp_x`|        110011xx'xxzzzzzz : enregistrer r(19+#X) paire à [sp-(#Z + 1) * 8] !, décalage préalable indexée > = -512 |
|`save_reg`|        110100xx'xxzzzzzz : enregistrer r(19+#X) reg à [sp + #Z * 8], décalage \<= 504 |
|`save_reg_x`|        x 1101010'xxxzzzzz : enregistrer r(19+#X) reg à [sp-(#Z + 1) * 8] !, décalage préalable indexée > = -256 |
|`save_lrpair`|         x 1101011'xxzzzzzz : enregistrer la paire \<r19 + 2 *#X, lr > à [sp + #Z*8], décalage \<= 504 |
|`save_fregp`|        x 1101100'xxzzzzzz : enregistrer d(8+#X) paire à [sp + #Z * 8], décalage \<= 504 |
|`save_fregp_x`|        x 1101101'xxzzzzzz : enregistrer d(8+#X) paire, [sp-(#Z + 1) * 8] !, décalage préalable indexée > = -512 |
|`save_freg`|        x 1101110'xxzzzzzz : enregistrer d(8+#X) reg à [sp + #Z * 8], décalage \<= 504 |
|`save_freg_x`|        11011110' xxxzzzzz : enregistrer d(8+#X) reg à [sp-(#Z + 1) * 8] !, décalage préalable indexée > = -256 |
|`alloc_l`|         11100000' xxxxxxxx 'xxxxxxxx' xxxxxxxx : allouer de la pile volumineuses avec taille \< M 256 (2 ^ 24 * 16) |
|`set_fp`|        11100001 : configurer r29 : avec : r29 mov, sp |
|`add_fp`|        11100010' xxxxxxxx : configurer r29 avec : ajoutez r29, sp, #x * 8 |
|`nop`|            11100011 : aucun déroulement de l’opération est nécessaire. |
|`end`|            11100100 : fin du code de déroulement. Implique ret dans l’épilogue. |
|`end_c`|        11100101 : fin du code de déroulement dans la portée chaînée actuelle. |
|`save_next`|        11100110 : Enregistrer suivant Int non volatile ou FP inscrire paire. |
|`arithmetic(add)`|    11100111' 000zxxxx : ajouter un cookie reg(z) à lr (0 = x28, 1 = sp) ; Ajouter lr, lr, reg(z) |
|`arithmetic(sub)`|    11100111' 001zxxxx : sub reg(z) de cookie à partir de lr (0 = x28, 1 = sp) ; Sub lr, lr, reg(z) |
|`arithmetic(eor)`|    11100111' 010zxxxx : lr eor avec cookie reg(z) (0 = x28, 1 = sp) ; EOR lr, lr, reg(z) |
|`arithmetic(rol)`|    11100111' 0110xxxx : rol simulé de lr avec reg cookie (x28) ; xip0 = neg x28 ; ROR lr, xip0 |
|`arithmetic(ror)`|    11100111' 100zxxxx : lr ror avec cookie reg(z) (0 = x28, 1 = sp) ; ROR lr, lr, reg(z) |
| |            11100111 : xxxz--- :---réservé |
| |              11101xxx : réservé pour les cas de pile personnalisée ci-dessous générés uniquement pour les routines asm |
| |              11101001: Pile personnalisée pour MSFT_OP_TRAP_FRAME |
| |              11101010: Pile personnalisée pour MSFT_OP_MACHINE_FRAME |
| |              11101011: Pile personnalisée pour MSFT_OP_CONTEXT |
| |              1111xxxx: reserved |

Dans les instructions avec des valeurs élevées couvrant plusieurs octets, les bits les plus significatifs sont enregistrés en premier. Les codes de déroulement ci-dessus soient conçus pour en recherchant simplement le premier octet du code, il est possible de connaître la taille totale en octets du code de déroulement. Étant donné que chaque code de déroulement est mappée exactement à une instruction de prologue/épilogue, pour calculer la taille du prologue ou de l’épilogue, doit être effectuée qu’à remonter à partir du début de la séquence à la fin, à l’aide d’une table de recherche ou un dispositif similaire pour déterminer la durée pendant laquelle le cor est de l’opcode répond.

Notez qu’addressing décalage postérieures indexée n’est pas autorisée dans le prologue. Toutes les plages d’offsets (#Z) correspond à l’encodage de STP/STR addressing sauf `save_r19r20_x` dans quels 248 est suffisante pour toutes les entités des zones (des registres Int 10 + 8 registres FP + 8 registres d’entrée).

`save_next` doit suivre un enregistrement pour Int ou volatile FP inscrire paire : `save_regp`, `save_regp_x`, `save_fregp`, `save_fregp_x`, `save_r19r20_x`, ou un autre `save_next`. Elle enregistre la paire de Registre suivante à la prochaine plage de 16 octets dans l’ordre « expansion ». `save-next` suivant une `save_next` qui désigne la dernière paire de Registre Int fait référence à la première paire de registres de virgule flottante.

Étant donné que la taille de regular retourner et instructions de saut de sont les mêmes, n’est pas nécessaire d’un séparées `end` code pour les scénarios d’appel tail de déroulement.

`end_c` est conçu pour traiter les fragments de fonction non contigus fins d’optimisation. Un `end_c` qui indique la fin de codes de déroulement dans la portée actuelle doit être suivie d’une autre série de code de déroulement s’est terminée avec une véritable `end`. Les codes de déroulement entre `end_c` et `end` représentent les opérations de prologue dans la zone parente (prologue « fantôme »).  Plus de détails et d’exemples sont décrites dans la section ci-dessous.

### <a name="packed-unwind-data"></a>Emballés données de déroulement

Pour les fonctions emballées dont suivi les prologues et épilogues la forme canonique décrite ci-dessous, déroulement données peuvent être utilisées, éliminant la nécessité d’un enregistrement .xdata entièrement et ce qui réduit considérablement le coût de la fourniture de données de déroulement. Le canoniques prologues et épilogues sont conçus pour répondre aux besoins courants d’une fonction simple qui ne nécessite pas d’un gestionnaire d’exceptions, et qui effectue ses opérations setup et teardown dans un ordre standard.

Le format d’un enregistrement .pdata avec compressé de déroulement données ressemble à ceci :

![données de déroulement enregistrement .pdata avec compressé](media/arm64-exception-handling-packed-unwind-data.png "enregistrement .pdata avec compressée des données de déroulement")

Les champs sont les suivantes :

- **Fonction RVA Démarrer** est l’adresse RVA 32 bits du début de la fonction.
- **Indicateur** est un champ de 2 bits comme décrit ci-dessus, avec les significations suivantes :
  - 00 = compressé déroulement des données non utilisées ; bits restants pointent vers un enregistrement .xdata, ci-dessous
  - 01 = compressée utilisées comme décrit ci-dessous, avec un seul prologue et épilogue au début et à la fin de l’étendue des données de déroulement
  - 10 = compressée utilisées comme décrit ci-dessous pour le code sans prologue et épilogue ; des données de déroulement Cela est utile pour décrire les segments de la fonction séparés.
  - 11 = réservés ;
- **Longueur de la fonction** est un champ de 11 bits fournissant la longueur de la fonction entière en octets, divisé par 4. Si la fonction est supérieure à 8 Ko, un enregistrement .xdata complet doit être utilisé à la place.
- **La taille de trame** est un champ de 9 bits indiquant le nombre d’octets de pile est allouée pour cette fonction, divisée par 16. Les fonctions qui allouent supérieure (8k-16) des octets de pile doivent utiliser un enregistrement .xdata complet. Cela inclut le réseau local variable, sortant de zone de paramètres, enregistrées par l’appelé Int et FP zone et zone de paramètres de base, mais à l’exclusion de la zone d’allocation dynamique.
- **CR** est un indicateur de 2 bits qui indique si la fonction inclut des instructions supplémentaires pour définir une chaîne de frames et un lien de retour :
  - 00 = fonction non chaînée, \<r29, lr > paire n’est pas enregistrée dans la pile.
  - 01 = fonction non chaînée, \<lr > est enregistré dans la pile
  - 10 = réservés ;
  - 11 = fonction chaînée, une instruction de paire de magasin/charge est utilisée dans le prologue/épilogue \<r29, lr >
- **H** est un indicateur de 1 bit qui indique si la fonction héberge le paramètre entier inscrit (r0-r7) en les stockant dès le début de la fonction. (0 = n’héberge pas les registres, 1 = héberge les registres).
- **RegI** est un champ de 4 bits indiquant le nombre d’INT les registres non volatils (r19 r28) enregistré dans l’emplacement de pile canonique.
- **RegF** est un champ de 3 bits indiquant le nombre de FP les registres non volatils (d8-d15) enregistré dans l’emplacement de pile canonique. (0 ne = aucune FP register est enregistré, m > 0 : m + 1 registres de virgule flottante sont enregistrés). Pour la fonction enregistrer qu’un seul registre FP, conditionné de déroulement données ne peut pas être appliquées.

Les prologues canoniques qui appartiennent aux catégories 1, 2 (sans zone de paramètres sortants), 3 et 4 dans la section ci-dessus peuvent être représentés par le format de déroulement compressé.  Les épilogues pour les fonctions canoniques suivent une forme très similaire, sauf **H** n’a aucun effet, la `set_fp` instruction est omise, ainsi que l’ordre des étapes, ainsi que des instructions dans chaque étape dans l’épilogue. L’algorithme pour xdata compressé suit ces étapes détaillées dans le tableau suivant :

Étape 0 : Effectuer le calcul préalable de la taille de chaque zone.

Étape 1 : Enregistrer des registres enregistrés des appelés de Int.

Étape 2 : Cette étape est spécifique de type 4 dans les premières sections. LR est enregistré à la fin de la zone de type Int.

Étape 3 : Enregistrer des registres enregistrés des appelés FP.

Étape 4 : Enregistrer des arguments d’entrée dans la zone paramètre domestique.

Étape 5 : Allouer de la pile restante, y compris le réseau local, \<r29, lr > paire et zone de paramètres sortants. 5 a correspond au type canonique 1. 5 b et c de 5 sont pour le type canonique 2. 5D 5e concernent à la fois type 3 et tapez 4.

Étape #|Valeurs d’indicateur|nombre d’instructions|Opcode|Code de déroulement
-|-|-|-|-
0|||`#intsz = RegI * 8;`<br/>`if (CR==01) #intsz += 8; // lr`<br/>`#fpsz = RegF * 8;`<br/>`if(RegF) #fpsz += 8;`<br/>`#savsz=((#intsz+#fpsz+8*H)+0xf)&~0xf)`<br/>`#locsz = #famsz - #savsz`|
1|0 < **regI** < = 10|RegI / 2 + **RegI** % 2|`stp r19,r20,[sp,#savsz]!`<br/>`stp r21,r22,[sp,16]`<br/>`...`|`save_regp_x`<br/>`save_regp`<br/>`...`
2|**CR**==01*|1|`str lr,[sp, #intsz-8]`\*|`save_reg`
3|0 < **RegF** <=7|(RegF + 1) / 2 +<br/>(RegF + 1) % 2).|`stp d8,d9,[sp, #intsz]`\*\*<br/>`stp d10,d11,[sp, #intsz+16]`<br/>`...`<br/>`str d(8+RegF),[sp, #intsz+#fpsz-8]`|`save_fregp`<br/>`...`<br/>`save_freg`
4|**H** == 1|4|`stp r0,r1,[sp, #intsz+#fpsz]`<br/>`stp r2,r3,[sp, #intsz+#fpsz+16]`<br/>`stp r4,r5,[sp, #intsz+#fpsz+32]`<br/>`stp r6,r7,[sp, #intsz+#fpsz+48]`|`nop`<br/>`nop`<br/>`nop`<br/>`nop`
5a|**CR** == 11 && #locsz<br/> <= 512|2|`stp r29,lr,[sp,-#locsz]!`<br/>`mov r29,sp`\*\*\*|`save_fplr_x`<br/>`set_fp`
5b|**CR** == 11 &&<br/>512 < #locsz <= 4088|3|`sub sp,sp, #locsz`<br/>`stp r29,lr,[sp,0]`<br/>`add r29, sp, 0`|`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5c|**CR** == 11 && #locsz > 4088|4|`sub sp,sp,4088`<br/>`sub sp,sp, (#locsz-4088)`<br/>`stp r29,lr,[sp,0]`<br/>`add r29, sp, 0`|`alloc_m`<br/>`alloc_s`/`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5d|(**CR** == 00 \|\| **CR**==01) &&<br/>#locsz <= 4088|1|`sub sp,sp, #locsz`|`alloc_s`/`alloc_m`
5e|(**CR** == 00 \|\| **CR**==01) &&<br/>#locsz > 4088|2|`sub sp,sp,4088`<br/>`sub sp,sp, (#locsz-4088)`|`alloc_m`<br/>`alloc_s`/`alloc_m`

\* Si **CR** == 01 et **RegI** est un nombre impair, étape 2 et dernière save_rep à l’étape 1 sont fusionnées dans un save_regp.

\*\* Si **RegI** == **CR** == 0, et **RegF** ! = 0, le premier protocole stp pour la virgule flottante ne la décrémentation préfixée.

\*\*\* Aucune instruction correspondant à `mov r29, sp` est présent dans l’épilogue. Si une fonction requiert la restauration de procédure stockée à partir de r29 ensuite nous ne pouvons pas utiliser emballés données de déroulement.

### <a name="unwinding-partial-prologs-and-epilogs"></a>Épilogues et le déroulement des prologues partielles

La situation de déroulement plus courante est une où l’appel ou une exception s’est produite dans le corps de la fonction, le prologue et tous les épilogues. Dans ce cas, le déroulement est simple : le dérouleur simplement commence les codes dans le tableau de déroulement, commençant à l’index 0 et en continuant jusqu'à ce qu’un opcode de fin est détecté.

Il est plus difficile de se dérouler correctement dans le cas où une exception ou une interruption se produit lors de l’exécution d’un prologue ni épilogue. Dans ces situations, le frame de pile n'est que partiellement construit, et l’astuce consiste à déterminer exactement ce qui a été fait pour l’annuler correctement.

Par exemple, prenez cette séquence de prologue et épilogue :

```asm
0000:    stp    r29, lr, [sp, -256]!        // save_fplr_x  256 (pre-indexed store)
0004:    stp    d8,d9,[sp,224]              // save_fregp 0, 224
0008:    stp    r19,r20,[sp,240]            // save_regp 0, 240
000c:    mov    r29,sp                      // set_fp
         ...
0100:    mov    sp,r29                      // set_fp
0104:    ldp    r19,r20,[sp,240]            // save_regp 0, 240
0108:    ldp    d8,d9,[sp,224]              // save_fregp 0, 224
010c:    ldp    r29, lr, [sp, -256]!        // save_fplr_x  256 (post-indexed load)
0110:    ret     lr                         // end
```

En regard de chaque opcode est le code de déroulement approprié qui décrit cette opération. La première chose à noter est que la série de codes de déroulement du prologue est une image miroir exacte de codes de déroulement de l’épilogue (sans compter l’instruction finale de l’épilogue). Il s’agit d’une situation courante, et c’est pourquoi le déroulement codes pour le prologue sont toujours considérées comme être stockées dans l’ordre inverse à partir de l’ordre d’exécution du prologue.

Par conséquent, pour le prologue et épilogue, nous restons confrontés à un ensemble commun de codes de déroulement :

`set_fp`, `save_regp 0,240`, `save_fregp,0,224`, `save_fplr_x_256`, `end`

À partir de la casse de l’épilogue (plus simple car il est dans l’ordre normal), au décalage 0 dans l’épilogue (qui démarre au décalage 0 x 100 dans la fonction), on attendait exécuter la séquence de déroulement complète, comme aucun nettoyage n’a encore été effectuée. Si nous nous trouvons une seule instruction dans (à l’offset 2 dans l’épilogue), nous pouvons procéder au déroulement en ignorant le premier code de déroulement. La généralisation de cette situation, en supposant qu’un mappage 1:1 entre les opcodes et codes de déroulement, nous pouvons d’état que si nous sommes le déroulement démarre à partir de n instruction dans l’épilogue, nous devons ignorer les codes de déroulement n premier et commencer l’exécution à partir de là.

Il s’avère qu’une logique similaire fonctionne pour le prologue, à l’exception dans l’ordre inverse. Si nous sommes le déroulement démarre à partir de l’offset 0 dans le prologue, nous voulons exécuter rien. Si nous déroulée décalage 2, qui est la première instruction, puis nous voulons démarrer l’exécution du code de déroulement un déroulement séquence à partir de la fin (n’oubliez pas, les codes sont stockés dans l’ordre inverse). Et ici trop nous pouvons généraliser que si nous sommes le déroulement démarre à partir de n instruction dans le prologue, nous devons démarrer l’exécution de codes de déroulement n à partir de la fin de la liste des codes.

À présent, il n’est pas toujours le cas où les codes de prologue et épilogue correspondent exactement. Pour cette raison, le tableau de déroulement devons peut contenir plusieurs séquences de codes. Pour déterminer le décalage de l’emplacement où commencer le traitement des codes, utilisez la logique suivante :

1. Si le déroulement démarre dans le corps de la fonction, simplement commencer l’exécution de codes de déroulement à l’index 0 et continuer jusqu'à atteindre un opcode de « fin ».

1. Si le déroulement démarre dans un épilogue, utilisez l’index de départ spécifique à l’épilogue fourni avec la portée d’épilogue comme point de départ. Calculer le nombre d’octets le PC en question est à partir du début de l’épilogue. Avancer vers l’avant via les codes de déroulement, en ignorant les codes de déroulement jusqu'à ce que toutes les instructions déjà exécutées sont pris en compte. Puis exécutez en commençant à ce stade.

1. Si le déroulement démarre dans le prologue, utilisez l’index 0 comme point de départ. Calculer la longueur du code de prologue de la séquence et vous devez calculer le nombre d’octets le PC en question est à la fin du prologue. Avancer vers l’avant via les codes de déroulement, en ignorant les codes de déroulement jusqu'à ce que toutes les instructions non encore exécutés sont pris en compte. Puis exécutez en commençant à ce stade.

Par conséquent de ces règles, les codes de déroulement du prologue doivent toujours être le premier dans le tableau, et ils sont également les codes de déroulement général déroulements dans le corps. Les séquences de code spécifique à l’épilogue doivent suivre immédiatement.

### <a name="function-fragments"></a>Fragments de fonction

Pour des raisons de l’optimisation de code et d’autres raisons, il peut être préférable de scinder une fonction en fragments séparés (également appelés régions). Dans ce cas, chaque fragment de fonction qui en résulte exige son propre distinct .pdata (et éventuellement .xdata) enregistrement.

Pour séparées fragment secondaire qui a son propre prologue, il est probable qu’aucun ajustement de pile ne s’effectue par son prologue. Tout espace requis par la base de données secondaire de pile régions doivent être pré-allouée par son parent (ou région région appelé hôte). Cela permet de conserver les manipulations de pointeur de pile strictement dans le prologue d’origine de la fonction.

Un cas ordinaire de fragments de fonction est « séparation de code » avec ce compilateur peut déplacer une région de code en dehors de sa fonction de l’hôte. Il existe trois cas inhabituels qui a pu être provoqués par la séparation de code.

#### <a name="example"></a>Exemple :

- (zone 1 : commencer)

    ```asm
        stp     r29, lr, [sp, -256]!    // save_fplr_x  256 (pre-indexed store)
        stp     r19,r20,[sp,240]        // save_regp 0, 240
        mov     r29,sp                  // set_fp
        ...
    ```

- (zone 1 : fin)
- (zone 3 : commencer)

    ```asm
        ...
    ```

- (zone 3 : fin)
- (zone 2 : commencer)

    ```asm
    ...
        mov     sp,r29                  // set_fp
        ldp     r19,r20,[sp,240]        // save_regp 0, 240
        ldp     r29, lr, [sp, -256]!    // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- (zone 2 : fin)

1. Prologue uniquement (région 1 : tous les épilogues se trouvent dans des régions séparées) :

   Uniquement dans le prologue doit être décrit. Ceci ne peut pas être représenté par .pdata compact format. Dans le cas .xdata complet, il peut être représenté en définissant le nombre d’épilogue = 0. Consultez la région 1 dans l’exemple ci-dessus.

   Codes de déroulement : `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end`.

1. Épilogues uniquement (région 2 : prologue est dans la région de l’hôte)

   Il est supposé que par le contrôle de temps passer à cette région, tous les codes de prologue ont été exécutées. Déroulement partiel peut se produire dans les épilogues la même façon que dans une fonction normale. Ce type de région ne peut pas être représenté par .pdata compact. Dans l’enregistrement xdata complète, il peut être encodé avec un prologue « fantôme », encadrée par une `end_c` et `end` paire de code de déroulement.  Le caractère de début `end_c` indique la taille du prologue est égal à zéro. Épilogue démarrer index des points épilogue unique à `set_fp`.

   Code de région 2 de déroulement : `end_c`, `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end`.

1. Aucun prologues ou les épilogues (zone 3 : les prologues et épilogues tous sont dans d’autres fragments) :

   Format de .pdata Compact peut être appliquée via la définition d’indicateur = 10. Avec l’enregistrement .xdata complet, nombre d’épilogue = 1. Déroulement code est le même que pour la région 2 ci-dessus, mais les Index de début d’épilogue pointe également vers `end_c`. Déroulement partiel se produira jamais dans cette région de code.

Un autre cas plus complexe de fragments de fonction est « réduire d’habillage » avec ce compilateur peut choisir de différer l’enregistrement des registres enregistrés appelé jusqu'à ce qu’en dehors du prologue d’entrée de fonction.

- (zone 1 : commencer)

    ```asm
        stp     r29, lr, [sp, -256]!    // save_fplr_x  256 (pre-indexed store)
        stp     r19,r20,[sp,240]        // save_regp 0, 240
        mov     r29,sp                  // set_fp
        ...
    ```

- (zone 2 : commencer)

    ```asm
        stp     r21,r22,[sp,224]        // save_regp 2, 224
        ...
        ldp     r21,r22,[sp,224]        // save_regp 2, 224
    ```

- (zone 2 : fin)

    ```asm
        ...
        mov     sp,r29                  // set_fp
        ldp     r19,r20,[sp,240]        // save_regp 0, 240
        ldp     r29, lr, [sp, -256]!    // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- (zone 1 : fin)

Dans le prologue de la région 1, l’espace de pile est alloué au préalable. Notez que cette région 2 ont le même code de déroulement que même s’il est déplacé en dehors de sa fonction de l’hôte.

Zone 1 : `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end` avec Index de début d’épilogue pointe vers `set_fp` comme d’habitude.

Zone 2 : `save_regp 2, 224`, `end_c`, `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end`. Index de début d’épilogue pointe pour le code de déroulement tout d’abord `save_regp 2, 224`.

### <a name="large-functions"></a>Fonctions volumineuses

Fragments peuvent être exploitées pour décrire les fonctions dont la taille dépasse la limite de 1 million imposée par les champs de bits dans l’en-tête .xdata. Pour décrire une fonction très volumineuse comme cela, elle doit simplement être divisé en fragments inférieure à 1 million. Chaque fragment doit être ajusté afin qu’il ne divise pas un épilogue en plusieurs parties.

Seul le premier fragment de la fonction contiendra un prologue ; tous les autres fragments sont marqués comme n’ayant aucune prologue. Selon le nombre d’épilogues présent, chaque fragment peut contenir zéro ou plusieurs épilogues. N’oubliez pas que chaque portée d’épilogue dans un fragment spécifie son décalage de départ par rapport au début du fragment, et non au début de la fonction.

Si un fragment ne contient aucun prologue et aucun épilogue, elle nécessite toujours ses propres .pdata (et éventuellement .xdata) enregistrement, de décrire le déroulement à partir du corps de la fonction.

## <a name="examples"></a>Exemples

### <a name="example-1-frame-chained-compact-form"></a>Exemple 1 : Forme compact frame en série

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

### <a name="example-2-frame-chained-full-form-with-mirror-prolog--epilog"></a>Exemple 2 : Frame en série, forme complète avec miroir prologue et épilogue

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

Notez que l’EpilogStart Index [0] pointe vers la même séquence de code de déroulement de prologue.

### <a name="example-3-variadic-unchained-function"></a>Exemple 3 : Variadiques chaîné (fonction)

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

Remarque : EpilogStart Index [4] pointe vers le milieu de code de déroulement de prologue (partiellement un tableau de déroulement de réutilisation).

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble des conventions ABI de ARM64](arm64-windows-abi-conventions.md)<br/>
[Gestion des exceptions ARM](arm-exception-handling.md)
