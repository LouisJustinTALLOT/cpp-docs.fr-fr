---
description: 'En savoir plus sur : vue d’ensemble des conventions ABI ARM64'
title: Vue d’ensemble des conventions ABI ARM64
ms.date: 03/27/2019
ms.openlocfilehash: d597a50b771524b69ef2f2091082d7ca4d19d453
ms.sourcegitcommit: e71b8da6c8a357aa06bb6b36936a8f4ecae082ad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97976334"
---
# <a name="overview-of-arm64-abi-conventions"></a>Vue d’ensemble des conventions ABI ARM64

L’interface binaire d’application (ABI) de base pour Windows lorsqu’elle est compilée et exécutée sur des processeurs ARM en mode 64 bits (architectures ARMv8 ou ultérieures), pour la plupart, suit le interface EABI AArch64 standard de ARM. Cet article met en évidence certaines des hypothèses principales et les modifications apportées par rapport à ce qui est documenté dans le interface EABI. Pour plus d’informations sur l’ABI 32 bits, consultez [vue d’ensemble des conventions Abi ARM](overview-of-arm-abi-conventions.md). Pour plus d’informations sur le interface EABI ARM standard, consultez [interface binaire d’application (ABI) pour l’architecture ARM](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.subset.swdev.abi/index.html) (lien externe).

## <a name="definitions"></a>Définitions

Avec l’introduction de la prise en charge de 64 bits, ARM a défini plusieurs termes :

- **AArch32** : architecture du jeu d’instructions 32 bits héritée (ISA) définie par ARM, y compris l’exécution en mode Thumb.
- **AArch64** : la nouvelle architecture de jeu d’instructions 64 bits (ISA) définie par ARM.
- **ARMv7** : spécification du matériel ARM « septième génération », qui comprend uniquement la prise en charge de AArch32. Cette version du matériel ARM est la première version prise en charge par Windows pour ARM.
- **ARMv8** : spécification du matériel ARM de 8 générations, qui comprend la prise en charge de AArch32 et AArch64.

Windows utilise également les termes suivants :

- **ARM** : fait référence à l’architecture ARM 32 bits (AArch32), parfois appelée WoA (Windows on ARM).
- **ARM32** – identique à ARM, ci-dessus ; utilisé dans ce document pour plus de clarté.
- **ARM64** : fait référence à l’architecture ARM 64 bits (AArch64). Il n’y a pas d’WoA64.

Enfin, lorsque vous faites référence aux types de données, les définitions suivantes de ARM sont référencées :

- **Short-Vector** : type de données directement représentable dans SIMD, vecteur de 8 octets ou 16 octets d’éléments. Elle est alignée sur une taille de 8 octets ou 16 octets, où chaque élément peut être 1, 2, 4 ou 8 octets.
- **HFA (agrégat à virgule flottante homogène)** : type de données avec 2 à 4 membres à virgule flottante identiques, flottant ou double.
- **HVA (agrégation homogène Short-Vector)** : type de données avec 2 à 4 membres Short-Vector identiques.

## <a name="base-requirements"></a>Configuration de base requise

La version ARM64 de Windows suppose qu’elle s’exécute à tout moment sur une architecture ARMv8 ou ultérieure. La prise en charge de la virgule flottante et du néon est supposée être présente dans le matériel.

La spécification ARMv8 décrit les nouveaux OpCodes de chiffrement et d’assistance CRC facultatifs pour AArch32 et AArch64. La prise en charge est actuellement facultative, mais recommandée. Pour tirer parti de ces opcodes, les applications doivent d’abord effectuer des contrôles d’exécution en vue de leur existence.

## <a name="endianness"></a>Endianness

Comme avec la version ARM32 de Windows, sur ARM64 Windows s’exécute en mode Little-endian. Le basculement de endianness est difficile à réaliser sans prise en charge du mode noyau dans AArch64. il est donc plus facile à mettre en œuvre.

## <a name="alignment"></a>Alignment

Windows s’exécutant sur ARM64 permet au matériel du processeur de gérer les accès non alignés de manière transparente. Dans le cas d’une amélioration apportée par AArch32, cette prise en charge fonctionne également pour tous les accès d’entiers (y compris les accès à plusieurs mots) et pour les accès en virgule flottante.

Toutefois, les accès à la mémoire déplacée (périphérique) doivent toujours être alignés. Si le code peut lire ou écrire des données mal alignées à partir de la mémoire non mise en cache, il doit veiller à aligner tous les accès.

Alignement de la disposition par défaut pour les variables locales :

| Taille en octets | Alignement en octets |
| - | - |
| 1 | 1 |
| 2 | 2 |
| 3, 4 | 4 |
| > 4 | 8 |

Alignement de la disposition par défaut pour les valeurs globales et statiques :

| Taille en octets | Alignement en octets |
| - | - |
| 1 | 1 |
| 2 - 7 | 4 |
| 8 - 63 | 8 |
| >= 64 | 16 |

## <a name="integer-registers"></a>Registres d’entiers

L’architecture AArch64 prend en charge les registres d’entiers 32 :

| S’inscrire | Volatil ? | Role |
| - | - | - |
| x0 | Volatil | Registre des paramètres/brouillons 1, registre des résultats |
| x1-x 7 | Volatil | Paramètre/Registre de travail 2-8 |
| x8-x15 | Volatil | Registres de travail |
| X16-x17 | Volatil | Registres de travail intra-procédure-appel |
| x18 | Non volatil | Registre de la plateforme : en mode noyau, pointe vers KPCR pour le processeur actuel. en mode utilisateur, pointe vers TEB |
| x19-x28 | Non volatil | Registres de travail |
| x29/FP | Non volatil | Pointeur de frame |
| X30/LR | Non volatil | Lier les registres |

Chaque registre est accessible en tant que valeur 64 bits complète (via x0-X30) ou en tant que valeur 32 bits (via W0-W30). 32 bits opérations zéro-étendent leurs résultats jusqu’à 64 bits.

Consultez la section relative au passage de paramètres pour plus d’informations sur l’utilisation des registres de paramètres.

Contrairement à AArch32, le compteur de programme (PC) et le pointeur de pile (SP) ne sont pas des registres indexés. Ils sont limités dans la manière dont ils sont accessibles. Notez également qu’il n’y a pas de Registre x31. Cet encodage est utilisé à des fins spéciales.

Le pointeur de frame (x29) est requis pour la compatibilité avec le parcours de pile rapide utilisé par ETW et d’autres services. Il doit pointer vers la paire {x29, X30} précédente sur la pile.

## <a name="floating-pointsimd-registers"></a>Registres à virgule flottante/SIMD

L’architecture AArch64 prend également en charge les registres à virgule flottante 32/SIMD, résumés ci-dessous :

| S’inscrire | Volatil ? | Role |
| - | - | - |
| v0 | Volatil | Registre des paramètres/brouillons 1, registre des résultats |
| v1-v7 | Volatil | Registres de paramètres/Scratch 2-8 |
| V8-v15 | Non volatil | Registres de travail (seuls les 64 bits de poids faible sont non volatils) |
| v16-v31 | Volatil | Registres de travail |

Chaque registre est accessible en tant que valeur 128 bits complète (via v0-V31 ou Q0-Q31). Elle est accessible en tant que valeur 64 bits (via D0-D31), sous la forme d’une valeur 32 bits (via S0-S31), en tant que valeur 16 bits (via H0-H31) ou en tant que valeur 8 bits (via B0-B31). Les accès inférieurs à 128 bits accèdent uniquement aux bits inférieurs du Registre 128 bits complet. Ils laissent intacts les bits restants, sauf indication contraire. (AArch64 est différent de AArch32, où les registres plus petits ont été regroupés en plus des registres plus volumineux.)

Le registre de contrôle à virgule flottante (FPCR) a certaines exigences sur les différents champs de bits qu’il contient :

| Bits | Signification | Volatil ? | Role |
| - | - | - | - |
| 26 | AHP | Non volatile | Autre contrôle à demi-précision. |
| 25 | DN | Non volatile | Contrôle en mode NaN par défaut. |
| 24 | FZ | Non volatil | Contrôle de mode de vidage à zéro. |
| 23-22 | RMode | Non volatil | Contrôle du mode d’arrondi. |
| 15, 12-8 | IDE/IXE/etc. | Non volatile | L’interruption d’exception active les bits, doit toujours être 0. |

## <a name="system-registers"></a>Registres système

Comme AArch32, la spécification AArch64 fournit trois registres « ID de thread » contrôlés par le système :

| S’inscrire | Role |
| - | - |
| TPIDR_EL0 | Réservé. |
| TPIDRRO_EL0 | Contient le nombre de processeurs pour le processeur actuel. |
| TPIDR_EL1 | Pointe vers la structure KPCR pour le processeur actuel. |

## <a name="floating-point-exceptions"></a>Exceptions à virgule flottante

La prise en charge des exceptions de virgule flottante IEEE est facultative sur les systèmes AArch64. Pour les variantes de processeur qui ont des exceptions de virgule flottante matérielle, le noyau Windows intercepte silencieusement les exceptions et les désactive implicitement dans le registre FPCR. Cette interruption garantit un comportement normalisé entre les variantes de processeur. Dans le cas contraire, le code développé sur une plateforme sans prise en charge des exceptions peut se retrouver en cas d’exceptions inattendues lors de l’exécution sur une plateforme avec prise en charge.

## <a name="parameter-passing"></a>Passage de paramètres

Pour les fonctions non variadiques, l’ABI Windows suit les règles spécifiées par ARM pour le passage de paramètres. Ces règles sont extraites directement de la norme d’appel de procédure pour l’architecture AArch64 :

### <a name="stage-a--initialization"></a>Étape A : initialisation

Cette étape est effectuée une seule fois, avant le début du traitement des arguments.

1. Le prochain numéro de Registre à usage général (NGRN) est défini à zéro.

1. Le numéro de Registre NSRN SIMD et à virgule flottante suivant est défini sur zéro.

1. L’adresse d’argument empilée suivante (adresse NSAA) est définie sur la valeur actuelle du pointeur de pile (SP).

### <a name="stage-b--pre-padding-and-extension-of-arguments"></a>Étape B : pré-remplissage et extension des arguments

Pour chaque argument de la liste, la première règle de correspondance de la liste suivante est appliquée. Si aucune règle ne correspond, l’argument est utilisé sans modification.

1. Si le type d’argument est un type composite dont la taille ne peut pas être déterminée de manière statique par l’appelant et l’appelé, l’argument est copié en mémoire et l’argument est remplacé par un pointeur vers la copie. (Il n’existe pas de tels types en C/C++, mais ils existent dans d’autres langages ou dans les extensions de langage).

1. Si le type d’argument est un HFA ou un HVA, l’argument est utilisé sans modification.

1. Si le type d’argument est un type composite supérieur à 16 octets, l’argument est copié dans la mémoire allouée par l’appelant, et l’argument est remplacé par un pointeur vers la copie.

1. Si le type d’argument est un type composite, la taille de l’argument est arrondie au multiple le plus proche de 8 octets.

### <a name="stage-c--assignment-of-arguments-to-registers-and-stack"></a>Phase C : assignation d’arguments aux registres et à la pile

Pour chaque argument de la liste, les règles suivantes sont appliquées tour à tour jusqu’à ce que l’argument ait été alloué. Quand un argument est assigné à un registre, les bits inutilisés dans le registre ont une valeur non spécifiée. Si un argument est assigné à un emplacement de pile, les octets de remplissage inutilisés ont une valeur non spécifiée.

1. Si l’argument est un type de vecteur à virgule flottante simple, double ou quadruple précision, et que le NSRN est inférieur à 8, l’argument est alloué aux bits les moins significatifs du Registre v \[ NSRN]. Le NSRN est incrémenté d’une unité. L’argument a maintenant été alloué.

1. Si l’argument est un HFA ou un HVA, et qu’il y a suffisamment de registres à virgule flottante et SIMD non alloués (NSRN + nombre de membres ≤ 8), l’argument est alloué aux registres SIMD et à virgule flottante, un registre par membre de HFA ou HVA. Le NSRN est incrémenté par le nombre de registres utilisés. L’argument a maintenant été alloué.

1. Si l’argument est un HFA ou un HVA, le NSRN est défini sur 8, et la taille de l’argument est arrondie au multiple le plus proche de 8 octets.

1. Si l’argument est un HFA, un HVA, un type à virgule flottante quadruple précision ou un type vectoriel Short, le adresse NSAA est arrondi à la valeur la plus grande de 8 ou l’alignement naturel du type de l’argument.

1. Si l’argument est un type à virgule flottante en demi-ou simple précision, la taille de l’argument est définie sur 8 octets. L’effet est comme si l’argument avait été copié sur les bits les moins significatifs d’un registre 64 bits, et les bits restants remplis avec des valeurs non spécifiées.

1. Si l’argument est un HFA, un HVA, un type à virgule flottante demi-, simple, double ou quadruple précision ou un type de vecteur Short, l’argument est copié dans la mémoire au niveau du adresse NSAA ajusté. L’adresse NSAA est incrémentée de la taille de l’argument. L’argument a maintenant été alloué.

1. Si l’argument est un type intégral ou pointeur, la taille de l’argument est inférieure ou égale à 8 octets, et NGRN est inférieur à 8, l’argument est copié vers les bits les moins significatifs dans x \[ NGRN]. Le NGRN est incrémenté d’une unité. L’argument a maintenant été alloué.

1. Si l’argument a un alignement de 16, le NGRN est arrondi au nombre pair suivant.

1. Si l’argument est un type intégral, que la taille de l’argument est égale à 16 et que NGRN est inférieur à 7, l’argument est copié dans x \[ NGRN] et x \[ NGRN + 1]. x \[ NGRN] doit contenir le double mot adressé à la limite inférieure de la représentation de la mémoire de l’argument. Le NGRN est incrémenté de deux. L’argument a maintenant été alloué.

1. Si l’argument est un type composite et que la taille dans les mots doubles de l’argument n’est pas supérieure à 8 NGRN, l’argument est copié dans des registres à usage général consécutifs, à partir de x \[ NGRN]. L’argument est passé comme s’il avait été chargé dans les registres à partir d’une adresse alignée sur deux mots, avec une séquence appropriée d’instructions LDR qui chargent des registres consécutifs à partir de la mémoire. Le contenu des parties inutilisées des registres n’est pas spécifié par cette norme. Le NGRN est incrémenté par le nombre de registres utilisés. L’argument a maintenant été alloué.

1. NGRN a la valeur 8.

1. Le adresse NSAA est arrondi à la valeur la plus grande de 8 ou l’alignement naturel du type de l’argument.

1. Si l’argument est un type composite, l’argument est copié dans la mémoire au niveau du adresse NSAA ajusté. L’adresse NSAA est incrémentée de la taille de l’argument. L’argument a maintenant été alloué.

1. Si la taille de l’argument est inférieure à 8 octets, la taille de l’argument est définie sur 8 octets. L’effet est comme si l’argument était copié sur les bits les moins significatifs d’un registre 64 bits, et les autres bits étaient remplis avec des valeurs non spécifiées.

1. L’argument est copié dans la mémoire au niveau du adresse NSAA ajusté. L’adresse NSAA est incrémentée de la taille de l’argument. L’argument a maintenant été alloué.

### <a name="addendum-variadic-functions"></a>Addendum : fonctions variadiques

Les fonctions qui acceptent un nombre variable d’arguments sont gérées différemment de ce qui précède, comme suit :

1. Toutes les composites sont traités de la même façon. aucun traitement spécial de HFAs ou HVA.

1. Les registres SIMD et à virgule flottante ne sont pas utilisés.

En fait, c’est la même chose que les règles C. 12 – C. 15 pour allouer des arguments à une pile imaginaire, où les 64 premiers octets de la pile sont chargés dans x0-x 7, et tous les arguments de pile restants sont placés normalement.

## <a name="return-values"></a>Valeurs retournées

Les valeurs intégrales sont retournées dans x0.

Les valeurs à virgule flottante sont retournées dans S0, D0 ou v0, selon le cas.

Un type est considéré comme un HFA ou un HVA si tous les éléments suivants sont pris en compte :

- Elle n’est pas vide,
- Elle n’a aucun constructeur par défaut ou de copie, aucun destructeur ou opérateur d’assignation non trivial.
- Tous ses membres ont le même type HFA ou HVA, ou les types float, double ou néon qui correspondent aux types HFA ou HVA des autres membres.

Les valeurs HFA et HVA avec quatre éléments ou moins sont retournées dans S0-S3, D0-D3 ou v0-v3, selon le cas.

Les types retournés par valeur sont gérés différemment selon qu’ils ont certaines propriétés et que la fonction est une fonction membre non statique. Types qui ont toutes ces propriétés,

- elles sont *agrégées* par la définition de la norme c++ 14, c’est-à-dire qu’elles n’ont pas de constructeurs fournis par l’utilisateur, de membres de données non statiques privés ou protégés, aucune classe de base et aucune fonction virtuelle.
- ils ont un opérateur d’assignation de copie trivial et
- ils ont un destructeur trivial,

et sont retournés par des fonctions non membres ou des fonctions membres statiques, utilisez le style de retour suivant :

- Les types inférieurs ou égaux à 8 octets sont retournés en x0.
- Les types inférieurs ou égaux à 16 octets sont retournés en x0 et x1, avec x0 contenant les 8 octets d’ordre inférieur.
- Pour les types supérieurs à 16 octets, l’appelant doit réserver un bloc de mémoire dont la taille et l’alignement sont suffisants pour contenir le résultat. L’adresse du bloc de mémoire doit être passée comme argument supplémentaire à la fonction dans x8. L’appelé peut modifier le bloc de mémoire résultant à tout moment pendant l’exécution de la sous-routine. L’appelé n’est pas obligatoire pour conserver la valeur stockée dans x8.

Tous les autres types utilisent la Convention suivante :

- L’appelant doit réserver un bloc de mémoire dont la taille et l’alignement sont suffisants pour contenir le résultat. L’adresse du bloc de mémoire doit être passée comme argument supplémentaire à la fonction dans x0, ou x1 si $this est passé en x0. L’appelé peut modifier le bloc de mémoire résultant à tout moment pendant l’exécution de la sous-routine. L’appelé retourne l’adresse du bloc de mémoire en x0.

## <a name="stack"></a>Pile

À la suite du ABI présenté par ARM, la pile doit rester alignée sur 16 octets à tout moment. AArch64 contient une fonctionnalité matérielle qui génère des erreurs d’alignement de la pile chaque fois que le SP n’est pas aligné sur 16 octets et qu’un chargement ou un magasin relatif à un SP est effectué. Windows s’exécute avec cette fonctionnalité activée à tout moment.

Les fonctions qui allouent 4 Ko ou plus de pile doivent s’assurer que chaque page avant la dernière page est touchée dans l’ordre. Cette action garantit qu’aucun code ne peut « effectuer une «Bond » sur» les pages de garde utilisées par Windows pour développer la pile. En général, le toucher est effectué par l' `__chkstk` assistance, qui a une convention d’appel personnalisée qui passe l’allocation de pile totale divisée par 16 dans x15.

## <a name="red-zone"></a>Zone rouge

La zone de 16 octets située juste en dessous du pointeur de pile actuel est réservée à une utilisation par des scénarios d’analyse et de mise à jour corrective dynamique. Cette zone permet d’insérer du code soigneusement créé qui stocke deux registres sur [SP, #-16] et les utilise temporairement à des fins arbitraires. Le noyau Windows garantit que ces 16 octets ne sont pas remplacés si une exception ou une interruption est effectuée, en mode utilisateur et en mode noyau.

## <a name="kernel-stack"></a>Pile du noyau

La pile en mode noyau par défaut dans Windows est de six pages (24k). Portez une attention particulière aux fonctions avec des mémoires tampons de pile volumineuses en mode noyau. Une interruption mal chronométrée peut se trouver avec peu de place et créer un contrôle de bogue de panique dans la pile.

## <a name="stack-walking"></a>Parcours de la pile

Le code dans Windows est compilé avec les pointeurs de frame activés ([/Oy-](reference/oy-frame-pointer-omission.md)) pour permettre une parcours de pile rapide. En général, x29 (FP) pointe sur le lien suivant dans la chaîne, qui est une paire {FP, LR}, indiquant le pointeur vers le frame précédent sur la pile et l’adresse de retour. Le code tiers est encouragé à activer les pointeurs de frame également, afin d’améliorer le profilage et le traçage.

## <a name="exception-unwinding"></a>Déroulement d’exception

Le déroulement au cours de la gestion des exceptions est assisté par l’utilisation de codes de déroulement. Les codes de déroulement sont une séquence d’octets stockés dans la section. XData du fichier exécutable. Ils décrivent le fonctionnement du prologue et de la épilogue de manière abstraite, de sorte que les effets du prologue d’une fonction peuvent être annulés en préparation de la sauvegarde dans le frame de pile de l’appelant. Pour plus d’informations sur les codes de déroulement, consultez [gestion des exceptions ARM64](arm64-exception-handling.md).

Le interface EABI ARM spécifie également un modèle de déroulement d’exception qui utilise des codes de déroulement. Toutefois, la spécification présentée est insuffisante pour le déroulement dans Windows, qui doit gérer les cas où l’ordinateur se trouve au milieu d’un prologue ou d’un épilogue de fonction.

Le code généré dynamiquement doit être décrit avec des tables de fonctions dynamiques via `RtlAddFunctionTable` et des fonctions associées, afin que le code généré puisse participer à la gestion des exceptions.

## <a name="cycle-counter"></a>Compteur de cycles

Tous les processeurs ARMv8 sont requis pour prendre en charge un registre de compteur de cycle, un registre 64 bits que Windows configure pour être lisible à n’importe quel niveau d’exception, y compris le mode utilisateur. Elle est accessible via le registre de PMCCNTR_EL0 spécial, à l’aide de l’opcode MSR dans le code assembleur, ou de l' `_ReadStatusReg` intrinsèque dans le code C/C++.

Le compteur de cycle ici est un compteur de cycle réel, et non une horloge murale. La fréquence de comptage varie en fonction de la fréquence du processeur. Si vous estimez que vous devez connaître la fréquence du compteur de cycles, vous ne devriez pas utiliser le compteur de cycle. Au lieu de cela, vous souhaitez mesurer l’heure de l’horloge, pour laquelle vous devez utiliser `QueryPerformanceCounter` .

## <a name="see-also"></a>Voir aussi

[Problèmes courants de migration ARM Visual C++](common-visual-cpp-arm-migration-issues.md)<br/>
[Gestion des exceptions ARM64](arm64-exception-handling.md)
