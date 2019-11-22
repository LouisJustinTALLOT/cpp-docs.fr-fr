---
title: Vue d'ensemble des conventions ABI ARM
ms.date: 07/11/2018
ms.assetid: 23f4ae8c-3148-4657-8c47-e933a9f387de
ms.openlocfilehash: 176aaaa17af1ce358255ca94eaccc7d5217f2a87
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303185"
---
# <a name="overview-of-arm32-abi-conventions"></a>Vue d’ensemble des conventions ABI ARM32

L'interface binaire d'application (ABI) pour le code compilé pour Windows sur processeurs ARM est basée sur l'interface EABI ARM standard. Cet article souligne les principales différences entre Windows on ARM et l'interface standard. Ce document traite de l’ABI ARM32. Pour plus d’informations sur le ABI ARM64, consultez [vue d’ensemble des conventions Abi ARM64](arm64-windows-abi-conventions.md). Pour plus d’informations sur le interface EABI ARM standard, consultez [interface binaire d’application (ABI) pour l’architecture ARM](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.subset.swdev.abi/index.html) (lien externe).

## <a name="base-requirements"></a>Exigences de base

Windows on ARM est censé toujours s'exécuter sur une architecture ARMv7. Une prise en charge de la virgule flottante sous la forme de VFPv3-D32 ou version ultérieure doit être présente dans le matériel. L'architecture VFP doit prendre en charge la virgule flottante à simple et double précision sur le matériel. Le runtime Windows ne prend pas en charge l'émulation de la virgule flottante pour permettre une exécution sur du matériel non VFP.

La prise en charge des extensions SIMD avancées (NEON), ce qui englobe à la fois les opérations sur nombres entiers et à virgule flottante, doit aussi être présente sur le matériel. Aucune prise en charge de l'émulation n'est fournie au moment de l'exécution.

Une prise en charge de la division d'entier (UDIV/SDIV) est vivement recommandée mais pas exigée. Les plateformes sans prise en charge de la division d’entier peuvent être pénalisées sur le plan des performances, car ces opérations doivent être interceptées et peut-être corrigées.

## <a name="endianness"></a>Endianness

Windows on ARM s'exécute en mode Little-Endian. Le compilateur MSVC et le Windows Runtime attendent tous les deux des données de Little-endian à tout moment. Bien que l'instruction SETEND de l'architecture de jeu d'instructions (ISA) ARM autorise même le code en mode utilisateur à modifier l'endianness actif, cette opération est déconseillée car dangereuse pour une application. Si une exception est générée en mode Big-Endian, le comportement est imprévisible et peut provoquer une erreur d'application en mode utilisateur ou une vérification d'erreur en mode noyau.

## <a name="alignment"></a>Alignement

Bien que Windows permette au matériel ARM de gérer les accès d'entiers non alignés de manière transparente, des erreurs d'alignement peuvent toujours être générées dans certaines situations. Suivez les règles d'alignement suivantes :

- Les charges et les magasins d'entiers de la taille d'un demi-mot (16 bits) et d'un mot (32 bits) n'ont pas besoin d'être alignés. Le matériel les gère avec efficacité et transparence.

- Les charges et les magasins à virgule flottante doivent être alignés. Le noyau gère les charges et les magasins non alignés de manière transparente, mais avec une surcharge significative.

- Les opérations doubles (LDRD/STRD) et multiples (LDM/STM) de charge et de magasin doivent être alignées. Le noyau gère la plupart de ces opérations de façon transparente, mais avec une surcharge significative.

- Tous les accès mémoire non mis en cache doivent être alignés, même dans le cas des accès à des entiers. Les accès non alignés provoquent une erreur d'alignement.

## <a name="instruction-set"></a>Jeu d'instructions

Le jeu d'instructions pour Windows on ARM est strictement limité à Thumb-2. L'ensemble du code exécuté sur cette plateforme est toujours censé démarrer et rester en mode Thumb. Une tentative de basculement vers le jeu d'instructions ARM hérité a des chances d'aboutir. Dans ce cas, les exceptions ou les interruptions qui se produisent peuvent provoquer une erreur d'application en mode utilisateur ou une vérification d'erreur en mode noyau.

L’une des conséquences indirectes de cette exigence est que tous les pointeurs de code doivent avoir le bit inférieur défini. De cette façon, quand ils sont chargés et qu’une branche est créée via BLX ou BX, le processeur reste en mode Thumb et n’essaie pas d’exécuter le code cible en tant qu’instructions ARM 32 bits.

### <a name="it-instructions"></a>Instructions IT

L'utilisation d'instructions IT dans le code Thumb-2 n'est pas autorisée, sauf dans ces cas précis :

- L'instruction IT ne peut être utilisée que pour modifier une instruction cible.

- L'instruction cible doit être une instruction 16 bits.

- L'instruction cible doit être l'une des suivantes :

   |Opcodes 16 bits|Class|Restrictions|
   |---------------------|-----------|------------------|
   |MOV, MVN|Déplacement|Rm != PC, Rd != PC|
   |LDR, LDR[S]B, LDR[S]H|Chargement à partir de la mémoire|Mais pas les formes littérales LDR|
   |STR, STRB, STRH|Stockage en mémoire||
   |ADD, ADC, RSB, SBC, SUB|Ajout ou soustraction|Mais pas les formes ADD/SUB SP, SP, imm7<br /><br /> Rm != PC, Rdn != PC, Rdm != PC|
   |CMP, CMN|Comparer|Rm != PC, Rn != PC|
   |MUL|Multiplication||
   |ASR, LSL, LSR, ROR|Décalage de bits||
   |AND, BIC, EOR, ORR, TST|Arithmétique au niveau du bit||
   |BX|Création de branche vers le registre|Rm != PC|

Bien que les UC ARMv7 actuelles ne puissent pas signaler l'utilisation de formes d'instructions interdites, cela devrait être le cas dans les futures générations. Si ces formes sont détectées, tout programme qui les utilise peut se terminer avec une exception d'instruction non définie.

### <a name="sdivudiv-instructions"></a>Instructions SDIV/UDIV

L'utilisation des instructions de division d'entier SDIV et UDIV est entièrement prise en charge, même sur les plateformes sans matériel natif pour les traiter. La surcharge par division SDIV ou UDIV sur un processeur Cortex-A9 est d'environ 80 cycles, qui s'ajoutent au temps de division global de 20 à 250 cycles, selon les entrées.

## <a name="integer-registers"></a>Registres d’entiers

Le processeur ARM prend en charge 16 registres d'entiers :

|Registre|Volatil ?|Rôle|
|--------------|---------------|----------|
|r0|Volatil|Paramètres, résultat, registre de travail 1|
|r1|Volatil|Paramètres, résultat, registre de travail 2|
|r2|Volatil|Paramètre, registre de travail 3|
|r3|Volatil|Paramètre, registre de travail 4|
|r4|Non volatil||
|r5|Non volatil||
|r6|Non volatil||
|r7|Non volatil||
|r8|Non volatil||
|r9|Non volatil||
|r10|Non volatil||
|r11|Non volatil|Pointeur de frame|
|r12|Volatil|Registre de travail d'appels intra-procédure|
|r13 (SP)|Non volatil|Pointeur de pile|
|r14 (LR)|Non volatil|Registre de liaison|
|r15 (PC)|Non volatil|Compteur de programme|

Pour plus d'informations sur l'utilisation des registres de paramètres et de valeurs de retour, consultez la section Passage de paramètres dans cet article.

Windows utilise r11 pour parcourir rapidement le frame de pile. Pour plus d'informations, consultez la section Exploration de pile. Du fait de cette exigence, r11 doit toujours pointer vers le lien le plus haut de la chaîne. N'utilisez pas r11 à des fins générales : votre code ne générera pas d'explorations de pile correctes pendant l'analyse.

## <a name="vfp-registers"></a>Registres VFP

Windows prend en charge uniquement les variantes ARM qui intègrent une prise en charge du coprocesseur VFPv3-D32. Cela signifie que les registres en virgule flottante sont toujours présents, qu'ils peuvent être considérés comme des transmetteurs de paramètres fiables, et que l'ensemble complet des 32 registres est disponible. Les registres VFP et leur fonction sont résumés dans ce tableau :

|Simples|Doubles|Quadruples|Volatil ?|Rôle|
|-------------|-------------|-----------|---------------|----------|
|s0-s3|d0-d1|q0|Volatil|Paramètres, résultat, registre de travail|
|s4-s7|d2-d3|q1|Volatil|Paramètres, registre de travail|
|s8-s11|d4-d5|q2|Volatil|Paramètres, registre de travail|
|s12-s15|d6-d7|q3|Volatil|Paramètres, registre de travail|
|s16-s19|d8-d9|q4|Non volatil||
|s20-s23|d10-d11|q5|Non volatil||
|s24-s27|d12-d13|q6|Non volatil||
|s28-s31|d14-d15|q7|Non volatil||
||d16-d31|q8-q15|Volatil||

Le tableau suivant illustre les champs de bits du registre d'état et de contrôle des nombres à virgule flottante (ou FPSCR, Floating-Point Status and Control Register) :

|Bits|Signification|Volatil ?|Rôle|
|----------|-------------|---------------|----------|
|31-28|NZCV|Volatil|Indicateurs d'état|
|27|QC|Volatil|Saturation cumulative|
|26|AHP|Non volatil|Contrôle demi-précision alternatif|
|25|DN|Non volatil|Contrôle du mode NaN par défaut|
|24|FZ|Non volatil|Contrôle du mode de remplacement par zéro (Flush-to-zero)|
|23-22|RMode|Non volatil|Contrôle du mode d'arrondi|
|21-20|Stride|Non volatil|Pas (« stride ») vectoriel, doit toujours être égal à 0|
|18-16|Len|Non volatil|Longueur de vecteur, doit toujours être égale à 0|
|15, 12-8|IDE, IXE, etc.|Non volatil|Bits d'activation de l'interception d'exceptions, doit toujours être égal à 0|
|7, 4-0|IDC, IXC, etc.|Volatil|Indicateurs d'exception cumulatifs|

## <a name="floating-point-exceptions"></a>Exceptions à virgule flottante

La plupart des matériels ARM ne prennent pas en charge les exceptions de virgule flottante IEEE. Sur les variantes de processeur qui comportent des exceptions de virgule flottante matérielles, le noyau Windows intercepte discrètement les exceptions et les désactive implicitement dans le registre FPSCR. Ceci est le gage d'un comportement normalisé entre les variantes de processeur. Sinon, le code développé sur une plateforme qui ne prend pas en charge les exceptions pourrait recevoir des exceptions inattendues quand il s'exécute sur une plateforme qui prend en charge les exceptions.

## <a name="parameter-passing"></a>Passage de paramètres

Pour les fonctions non variadiques, l’interface ABI de Windows on ARM suit les règles d’ARM en matière de passage de paramètres (extensions VFP et SIMD avancées comprises). Ces règles suivent la [norme d’appel de procédure pour l’architecture ARM](http://infocenter.arm.com/help/topic/com.arm.doc.ihi0042c/IHI0042C_aapcs.pdf), consolidée avec les extensions VFP. Par défaut, les quatre premiers arguments entiers et jusqu'à huit arguments à virgule flottante ou vectoriels sont passés aux registres, et des arguments supplémentaires sont passés à la pile. Les arguments sont assignés aux registres ou à la pile à l’aide de cette procédure :

### <a name="stage-a-initialization"></a>Étape A : initialisation

L’initialisation est exécutée une seule fois exactement, avant le début du traitement des arguments :

1. Le numéro NCRN (Next Core Register Number) est défini sur r0.

1. Les registres VFP sont marqués comme non alloués.

1. L’adresse NSAA (Next Stacked Argument Address) est définie sur le pointeur de pile (SP) actif.

1. Si une fonction qui retourne un résultat en mémoire est appelé, l'adresse du résultat est placée dans r0 et le numéro NCRN est défini sur r1.

### <a name="stage-b-pre-padding-and-extension-of-arguments"></a>Étape B : pré-remplissage et extension des arguments

Pour chaque argument de la liste, la première règle correspondante de la liste suivante est appliquée :

1. Si l'argument est un type composite dont la taille ne peut pas être statiquement déterminée à la fois par l'appelant et l'appelé, l'argument est copié en mémoire et remplacé par un pointeur vers la copie.

1. Si l'argument est un demi-mot d'un octet ou de 16 bits, il est étendu en mot complet de 32 bits avec des zéros ou des signes et est traité comme un argument de 4 octets.

1. Si l'argument est un type composite, sa taille est arrondie au multiple de 4 supérieur le plus proche.

### <a name="stage-c-assignment-of-arguments-to-registers-and-stack"></a>Étape C : assignation d’arguments aux registres et à la pile

Pour chaque argument de la liste, les règles suivantes sont appliquées tour à tour jusqu’à ce que l’argument ait été alloué :

1. Si l’argument est de type VFP et qu’il y a suffisamment de registres VFP non alloués consécutifs du type approprié, l’argument est alloué à la séquence de registres ayant les numéros les plus petits.

1. Si l'argument est un type VFP, tous les registres non alloués restants sont marqués comme non disponibles. L'adresse NSAA est ajustée vers le haut jusqu'à ce qu'elle soit correctement alignée par rapport au type d'argument et que l'argument soit copié dans la pile à l'adresse NSAA ajustée. L’adresse NSAA est ensuite incrémentée de la taille de l’argument.

1. Si l’argument nécessite un alignement de 8 octets, le numéro NCRN est arrondi au numéro de registre pair supérieur.

1. Si la taille de l’argument dans les mots de 32 bits n’est pas supérieure à r4 moins le numéro NCRN, l’argument est copié dans les registres principaux, à partir du numéro NCRN, les bits de poids faible occupant les registres ayant les numéros les plus petits. Le numéro NCRN est incrémenté du nombre de registres utilisés.

1. Si le numéro NCRN est inférieur à r4 et que l'adresse NSAA est égale au pointeur de pile (SP), l'argument est partagé entre les registres principaux et la pile. La première partie de l’argument est copiée dans les registres principaux, à partir du numéro NCRN, jusqu’à r3 inclus. Le reste de l’argument est copié dans la pile, à partir de l’adresse NSAA. Le numéro NCRN est défini sur r4 et l’adresse NSAA est incrémentée de la taille de l’argument moins le montant passé aux registres.

1. Si l’argument nécessite un alignement de 8 octets, l’adresse NSAA est arrondie à l’adresse alignée de 8 octets supérieure.

1. L'argument est copié en mémoire à l'adresse NSAA. L’adresse NSAA est incrémentée de la taille de l’argument.

Les registres VFP ne sont pas utilisés pour les fonctions variadiques, et les règles 1 et 2 de la phase C sont ignorées. Autrement dit, une fonction variadique peut commencer par un push facultatif {r0-r3} pour ajouter les arguments de registre aux autres arguments éventuellement passés par l'appelant, puis accéder à la liste d'arguments entière directement à partir de la pile.

Les valeurs de type entier sont retournées dans r0, éventuellement étendues à r1 pour les valeurs de retour de 64 bits. Les valeurs de type virgule flottante VFP/NEON ou SIMD sont retournées dans s0, d0 ou q0, selon le cas.

## <a name="stack"></a>Stack

La pile doit toujours rester alignée sur 4 octets et être alignée sur 8 octets à n'importe quelle limite de fonction. Cela est nécessaire pour prendre en charge l'utilisation fréquente d'opérations à blocage sur les variables de pile 64 bits. L'interface EABI ARM déclare que la pile est alignée sur 8 octets dans n'importe quelle interface publique. Pour des raisons de cohérence, l'interface ABI de Windows on ARM considère les limites de fonction comme une interface publique.

Les fonctions qui doivent utiliser un pointeur de frame (par exemple, les fonctions qui appellent `alloca` ou qui modifient le pointeur de pile dynamiquement) doivent configurer le pointeur de frame dans le registre r11 du prologue des fonctions et le laisser inchangé jusqu'à l'épilogue. Les fonctions qui n'ont pas besoin d'un pointeur de frame doivent effectuer toutes les mises à jour de pile dans le prologue et laisser le pointeur de pile inchangé jusqu'à l'épilogue.

Les fonctions qui allouent 4 Ko ou plus dans la pile doivent s'assurer que chaque page précédant la dernière page fait l'objet d'une interaction tactile dans l'ordre. Cela garantit qu’aucun code ne peut « effectuer une «Bond » sur» les pages de garde utilisées par Windows pour développer la pile. En règle générale, cette tâche est assurée par l'assistance `__chkstk`, à laquelle est passé le total de l'allocation de pile en octets divisé par 4 dans r4, et qui retourne le montant d'allocation de pile final en octets à r4.

### <a name="red-zone"></a>Zone rouge

La zone de 8 octets située juste en dessous du pointeur de pile actif est réservée à l'analyse et à la mise à jour corrective dynamique. Cela permet l'insertion de code généré avec soins, lequel stocke 2 registres au niveau de [sp, #-8] et les utilise provisoirement à des fins arbitraires. Le noyau Windows garantit que ces 8 octets ne seront pas remplacés si une exception ou une interruption se produit à la fois en mode utilisateur et en mode noyau.

### <a name="kernel-stack"></a>Pile du noyau

La pile par défaut du mode noyau de Windows représente trois pages (12 Ko). Veillez à ne pas créer de fonctions dotées de mémoires tampons de pile volumineuses en mode noyau. Une interruption pourrait se produire avec une hauteur de pile très basse et entraîner une vérification d'erreur de pile précipitée.

## <a name="cc-specifics"></a>C/C++ spécificités

Les énumérations sont des types d'entier de 32 bits sauf si au moins une valeur de l'énumération nécessite un stockage de double mot de 64 bits. Dans ce cas, l'énumération est promue en un type d'entier de 64 bits.

`wchar_t` est défini comme équivalent à `unsigned short`, afin de préserver la compatibilité avec d’autres plateformes.

## <a name="stack-walking"></a>Parcours de la pile

Le code Windows est compilé avec les pointeurs de frame activés ([/Oy (omission du pointeur de frame)](reference/oy-frame-pointer-omission.md)) pour permettre un parcours de pile rapide. En général, le registre r11 pointe vers le lien suivant dans la chaîne, qui correspond à une paire {r11, lr} qui spécifie le pointeur vers le frame précédent de la pile et l'adresse de retour. Nous recommandons aussi l'activation des pointeurs de frame dans votre code pour un profilage et un traçage améliorés.

## <a name="exception-unwinding"></a>Déroulement d’exception

Le déroulement de la pile pendant le traitement des exceptions est assuré par l'utilisation de codes de déroulement. Les codes de déroulement correspondent à une séquence d'octets stockés dans la section .xdata de l'image exécutable. Ils décrivent l'opération du code de prologue et d'épilogue de la fonction de manière abstraite, ce qui permet d'annuler les effets du prologue d'une fonction en préparation du déroulement dans le frame de pile de l'appelant.

L'interface EABI ARM spécifie un modèle de déroulement d'exception qui utilise des codes de déroulement. Cependant, cette spécification ne suffit pas pour un déroulement dans Windows, qui doit gérer des cas où le processeur se situe au milieu du prologue ou de l'épilogue d'une fonction. Pour plus d’informations sur les données d’exception Windows sur ARM et le déroulement, consultez [gestion des exceptions ARM](arm-exception-handling.md).

Nous vous recommandons de décrire le code généré dynamiquement à l'aide des tables de fonctions dynamiques spécifiées dans les appels à `RtlAddFunctionTable` et les fonctions associées pour permettre au code généré de participer à la gestion des exceptions.

## <a name="cycle-counter"></a>Compteur de cycles

Si les processeurs ARM exécutant Windows sont tenus de prendre en charge un compteur de cycles, l'utilisation directe du compteur peut causer des problèmes. Pour éviter ces problèmes, Windows on ARM utilise un opcode non défini pour demander une valeur de compteur de cycles 64 bits normalisée. Dans du code C ou C++, utilisez l'intrinsèque `__rdpmccntr64` pour émettre l'opcode approprié ; dans un assembly, utilisez l'instruction `__rdpmccntr64`. La lecture du compteur de cycles prend environ 60 cycles sur un Cortex-A9.

Le compteur est un vrai compteur de cycles, pas une horloge ; ainsi, la fréquence de comptage varie selon la fréquence du processeur. Si vous voulez mesurer le temps d'horloge écoulé, utilisez `QueryPerformanceCounter`.

## <a name="see-also"></a>Voir aussi

[Problèmes courants de migration ARM Visual C++](common-visual-cpp-arm-migration-issues.md)<br/>
[Gestion des exceptions ARM](arm-exception-handling.md)
