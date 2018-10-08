---
title: Vue d’ensemble des conventions ABI de ARM64 | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 585fd757c18c3a7c09645b64656e6ef77cde6dca
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861381"
---
# <a name="overview-of-arm64-abi-conventions"></a>Vue d’ensemble des conventions ABI de ARM64

La base ABI pour Windows lors de la compilation et exécution sur les processeurs ARM en mode 64 bits (ARMv8 ou des architectures plus loin), pour la plupart des cas, suit standard AArch64 EABI d’ARM. Cet article met en évidence certaines des hypothèses clés et des modifications à la documentation dans l’interface EABI. Pour plus d’informations sur l’ABI 32 bits, consultez [conventions ABI de vue d’ensemble de ARM](overview-of-arm-abi-conventions.md). Pour plus d’informations sur l’interface EABI ARM standard, consultez [binaire Interface Application (ABI) pour l’Architecture ARM](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.subset.swdev.abi/index.html) (lien externe).

## <a name="definitions"></a>Définitions

Avec l’introduction de la prise en charge 64 bits, ARM a défini plusieurs termes :

- **AArch32** – l’instruction 32 bits héritée définie architecture (ISA) défini par ARM, y compris l’exécution en mode Thumb.
- **AArch64** – la nouvelle instruction 64-bit défini architecture (ISA) défini par ARM.
- **ARMv7** – la spécification de la « génération 7e » matériel ARM, qui inclut uniquement la prise en charge de AArch32. Il s’agit de la version du matériel ARM prises en charge de la première version de Windows pour ARM.
- **ARMv8** – la spécification de la « génération 8 » matériel ARM, qui inclut la prise en charge de AArch32 et AArch64.

Outre ces définitions, dans Windows nous utilisons ces termes :

- **ARM** – fait référence à l’architecture ARM de 32 bits (AArch32). Cela est parfois appelé WoA (Windows sur ARM).
- **ARM32** : identique à ARM, ci-dessus ; utilisé dans ce document par souci de clarté.
- **ARM64** – fait référence à l’architecture ARM de 64 bits (AArch64). Il n’existe aucun WoA64.

Enfin, lorsque vous faites référence aux types de données, les définitions suivantes à partir d’ARM sont référencées :

- **Vecteur court** – il s’agit d’un type de données qui est directement représentable dans SIMD ; par exemple, un vecteur de valeur de 8 ou 16 octets d’éléments, aligné à sa taille (octets 8 ou 16), où chaque élément peut être 1, 2, 4 ou 8 octets
- **HFA (nombres à virgule flottante homogène agrégat)** – il s’agit d’un type de données avec 2-4 à virgule flottante membres identiques (float ou double)
- **HVA (homogènes courte-vecteur agrégat)** – il s’agit d’un type de données avec les membres de vecteur de courte identiques 2-4

## <a name="base-requirements"></a>Exigences de base

La version ARM64 de Windows suppose qu’il s’exécute sur un ARMv8 ou architecture ultérieur à tout moment. Les deux à virgule flottante et la prise en charge NEON sont supposées être présente sur le matériel.

Bien que la spécification ARMv8 permet la prise en charge complète des applications de AArch32, il n’existe actuellement aucun plan pour prendre en charge les applications ARM32 existantes en cours d’exécution sur la version ARM64 de Windows (par exemple, aucun plan WOW64). Cela est susceptible de réévaluation à l’avenir, mais il est l’hypothèse de travail actuel.

La spécification ARMv8 décrit le nouveau chiffrement facultatif et CRC d’assistance opcodes pour AArch32 et AArch64. Prise en charge pour ces est actuellement facultative, mais recommandée. Code qui souhaitent tirer parti de ces opcodes doit effectuer des vérifications à l’exécution de leur existence.

## <a name="endianness"></a>Endianness

Comme avec la ARM32 version de Windows, sur ARM64 Windows s’exécute en mode little-endian. Commutation endianness est difficile à obtenir sans prise en charge du mode noyau dans AArch64, par conséquent, il est plus facile à appliquer.

## <a name="alignment"></a>Alignement

Windows s’exécutant sur ARM64 permet le matériel de processeur pour gérer les accès non alignés en toute transparence. Dans une amélioration par rapport à AArch32, cette prise en charge désormais fonctionne également pour tous les accès entier (y compris l’accès à plusieurs mots) et pour l’accès à virgule flottante.

Toutefois, les accès mémoire non mis en cache (périphérique) toujours doivent toujours être alignées. Cela signifie que si le code qui peut-être être appelé à lecture/écriture données mal alignées de la mémoire non mis en cache, il doit lire les choses sans échec et vous assurer que tous les accès sont alignées.

## <a name="integer-registers"></a>Registres d’entiers

L’architecture AArch64 prend en charge 32 registres d’entiers, résumées ci-dessous :

|Registre|Volatil ?|Rôle|
|-|-|-|
x0|Volatil|Paramètre/zéro inscrire 1, inscrire de résultat
X1-x7|Volatil|Register/zéro paramètre 2 à 8
x8-x15|Volatil|Registres de travail
x16-x17|Volatil|Registres de travail intra--appel de procédure
x18|Non volatil|Registre de plateforme : en mode noyau, pointe KPCR pour le processeur actuel ; en mode utilisateur, pointe vers TEB
x19-x28|Non volatil|Registres de travail
x29/fp|Non volatil|Pointeur de frame
x30/lr|Non volatil|Registres de lien

Chaque registre est accessible comme une valeur 64 bits (via x0-x30) ou comme une valeur 32 bits (via w0-w30). opérations de 32 bits zéro-étendent leurs résultats jusqu'à 64 bits.

Consultez le paramètre en passant de la section pour plus d’informations sur l’utilisation des registres de paramètre.

Notez que contrairement à AArch32, le PC et la procédure stockée ne sont pas indexées registres et par conséquent, sont limités dans la façon dont elles peuvent être accédées. Également Remarque qu’il n’existe aucun x31 inscrire (encodage est utilisé à des fins spéciales).

L’utilisation du pointeur frame (x29) est requise pour la compatibilité avec des parcours de pile rapide utilisée par ETW et d’autres services. Il doit pointer vers la précédente {x29, x 30} paire sur la pile.

## <a name="floating-pointsimd-registers"></a>Registres de virgule flottante/SIMD

L’architecture AArch64 prend également en charge 32 registres de virgule flottante/SIMD, résumées ci-dessous :

Registre|Volatil ?|Rôle
|-|-|-|
V0|Volatil|Paramètre/zéro inscrire 1, inscrire de résultat
V1-v7|Volatil|Paramètre/zéro inscrit 2 à 8
v8-v15|Non volatil|Scratch registres (Notez que seuls 64 bits de poids faibles sont non volatile)
V16-v31|Volatil|Registres de travail

Chaque registre est accessible en tant qu’une valeur 128 bits complète (via v0-v31 ou q0-q31), comme une valeur de 64 bits (via d0-d31), comme une valeur 32 bits (via s0-s31), comme une valeur de 16 bits (via h0-h31), ou comme une valeur de 8 bits (via b0-b31). Est inférieure à 128 bits accède à accéder uniquement les bits de poids faible du Registre de 128 bits et laisser les bits restants inchangés, sauf indication contraire. (Notez que cela diffère considérablement AArch32, où les registres plus petits ont été compressés sur les registres de plus grande).

Outre les registres de données, le Registre de contrôle à virgule flottante (FPCR) a certaines exigences sur les différents champs de bits qu’il contient :

Bits|Signification|Volatil ?|Rôle
|-|-|-|-|
26|AHP|Non Volatile|Contrôle demi-précision alternatif
25|DN|Non Volatile|Contrôle du mode NaN par défaut
24|FZ|Non volatil|Contrôle du mode de remplacement par zéro (Flush-to-zero)
23-22|RMode|Non volatil|Contrôle du mode d'arrondi
15,12-8|IDE/IXE/etc.|Non Volatile|Bits d'activation de l'interception d'exceptions, doit toujours être égal à 0

## <a name="system-registers"></a>Registres du système

Comme AArch32, la spécification AArch64 fournit trois contrôlés par le système « ID de thread » registres qui sont utilisés/allouée comme suit :

Registre|Rôle
|-|-|
TPIDR_EL0|Réservée
TPIDRRO_EL0|Contient le nombre d’UC pour le processeur actuel
TPIDR_EL1|Pointe vers une structure KPCR pour le processeur actuel

## <a name="floating-point-exceptions"></a>Exceptions de virgule flottante

Prise en charge des exceptions de virgule flottante IEEE est facultative sur les systèmes de AArch64. Pour les variantes de processeur qui n’ont pas les exceptions de virgule flottante matérielle, le noyau Windows intercepte discrètement les exceptions et les désactive implicitement dans le Registre FPCR. Il s’agit pour garantir un comportement normalisé entre les variantes de processeur (sinon, code développé sur une plateforme sans prise en charge de l’exception peut trouver lui-même en prenant des exceptions inattendues lors de l’exécution sur une plateforme avec prise en charge).

## <a name="parameter-passing"></a>Passage de paramètres

Pour les fonctions non variadiques, l’ABI de Windows suit les règles spécifiées par ARM pour le passage de paramètres. Ces règles sont extraites directement à partir de la norme d’appel de procédure pour l’Architecture AArch64 :

### <a name="stage-a--initialization"></a>Étape A : processus d’initialisation

Cette étape est effectuée une seule fois, avant le début du traitement des arguments.

1. Le prochain à usage général inscrire nombre (NGRN) est défini sur zéro.

1. La prochaine SIMD et nombre inscrire des nombres à virgule flottante (NSRN) est définie sur zéro.

1. L’adresse d’argument empilées suivante (NSAA) est définie à la valeur de pointeur de pile (SP) actuelle.

### <a name="stage-b--pre-padding-and-extension-of-arguments"></a>Étape B – remplissage préalable et extension des arguments

Pour chaque argument dans la liste la première règle correspondante dans la liste suivante est appliquée. Si aucune règle correspond à l’argument est utilisé sans modification.

1. Si le type d’argument est un Type Composite dont la taille ne peut pas être statiquement déterminée par l’appelant et l’appelé, l’argument est copié vers la mémoire et l’argument est remplacé par un pointeur vers la copie. (Il en existe aucun de ces types en C/C++, mais ils existent dans d’autres langues ou dans les extensions de langage).

1. Si le type d’argument est un HFA ou un HVA, l’argument est utilisé sans modification.

1. Si le type d’argument est un Type Composite qui est supérieure à 16 octets, puis l’argument est copié vers la mémoire allouée par l’appelant et l’argument est remplacé par un pointeur vers la copie.

1. Si le type d’argument est un Type Composite la taille de l’argument est arrondie au multiple plus proche de 8 octets.

### <a name="stage-c--assignment-of-arguments-to-registers-and-stack"></a>Étape C : assignation d’arguments aux registres et la pile

Pour chaque argument dans la liste les règles suivantes sont appliquées à son tour jusqu'à ce que l’argument a été alloué. Lorsqu’un argument est assigné à un Registre tous les bits inutilisés dans le Registre ont non spécifié de valeur. Lorsqu’un argument est affecté à un emplacement de pile les octets de remplissage non utilisés ont n’est pas spécifié valeur.

1. Si l’argument est un demi-, unique, Double ou quadruple-précision à virgule flottante ou Type vecteur court et le NSRN est inférieur à 8, puis l’argument est alloué pour les bits les moins significatifs v register [NSRN]. Le NSRN est incrémenté d’un. L’argument a maintenant été alloué.

1. Si l’argument est un HFA ou un HVA et il existe suffisamment SIMD non alloué et les registres en virgule flottante (NSRN + nombre de membres ≤ 8), l’argument est alloué à SIMD et inscrit les nombres à virgule flottante (avec un Registre par un membre du HFA ou HVA). Le NSRN est incrémenté par le nombre de registres utilisés. L’argument a maintenant été alloué.

1. Si l’argument est un HFA ou un HVA le NSRN est défini sur 8, puis la taille de l’argument est arrondie au multiple plus proche de 8 octets.

1. Si l’argument est un HFA, un HVA, un vecteur court ou à virgule flottante de précision de quatre cœurs tapez l’adresse NSAA est arrondi à la plus grande de 8 ou de l’alignement naturel de type de l’argument.

1. Si l’argument est un type virgule flottante de moitié ou simple précision, la taille de l’argument est définie à 8 octets. L’effet est comme si l’argument avait été copié vers les bits les moins significatifs d’un Registre 64 bits et les bits restants remplis avec des valeurs non spécifiées.

1. Si l’argument est un HFA, un HVA, un demi-, unique, Double - ou quadruple-précision à virgule flottante ou Type vecteur court, puis l’argument est copié dans la mémoire à l’adresse NSAA ajustée. L’adresse NSAA est incrémentée de la taille de l’argument. L’argument a maintenant été alloué.

1. Si l’argument est un entier ou un Type pointeur, la taille de l’argument est inférieur ou égal à 8 octets et le NGRN est inférieur à 8, l’argument est copié dans les bits les moins significatifs dans x [NGRN]. Le NGRN est incrémenté d’un. L’argument a maintenant été alloué.

1. Si l’argument possède un alignement de 16 puis le NGRN est arrondi par excès au nombre pair suivant.

1. Si l’argument est un Type intégral, la taille de l’argument est égale à 16, et le NGRN est inférieure à 7, l’argument est copié à x [NGRN] et [NGRN + 1]. x [NGRN] contient la plus faible adressée-mot double de la représentation sous forme de mémoire de l’argument. Le NGRN est incrémenté par deux. L’argument a maintenant été alloué.

1. Si l’argument est un Type Composite et la taille en mots doubles de l’argument n’est pas plus de 8 moins NGRN, l’argument est copié dans les registres à caractère général consécutifs, en commençant à x [NGRN]. L’argument est passé comme si elles avaient été chargées dans les registres depuis une adresse alignée à double mot avec une séquence d’instructions de LDR le chargement des registres consécutives de la mémoire (le contenu de tous les composants non utilisés des registres n’est pas spécifié appropriée par cette norme). Le NGRN est incrémenté par le nombre de registres utilisés. L’argument a maintenant été alloué.

1. Le NGRN a la valeur 8.

1. L’adresse NSAA est arrondie à la plus grande de 8 ou de l’alignement naturel de type de l’argument...

1. Si l’argument est un type composite l’argument est copié dans la mémoire à l’adresse NSAA ajustée. L’adresse NSAA est incrémentée de la taille de l’argument. L’argument a maintenant été alloué.

1. Si la taille de l’argument est inférieur à 8 octets la taille de l’argument est définie à 8 octets. L’effet est comme si l’argument a été copié dans les bits les moins significatifs d’un Registre 64 bits et les bits restants remplis avec des valeurs non spécifiées.

1. L’argument est copié dans la mémoire à l’adresse NSAA ajustée. L’adresse NSAA est incrémentée de la taille de l’argument. L’argument a maintenant été alloué.

### <a name="addendum-variadic-functions"></a>Addenda : Les fonctions Variadiques

Fonctions qui acceptent un nombre variable d’arguments sont gérées différemment de ceux ci-dessus, comme suit :

1. Composites tous les sont traités de la même façon ; aucun traitement spécial de HFAs ou Hva.

1. SIMD et inscrit les nombres à virgule flottante ne sont pas utilisés.

Effectivement, cela revient aux règles suivantes C.12–C.15 pour allouer des arguments à une pile imaginaire, où les 64 premiers octets de la pile sont chargés dans x0-x7, et tous les autres arguments pile sont placés normalement.

## <a name="return-values"></a>Valeurs de retour

Valeurs intégrales sont retournées dans x0. Les valeurs à virgule flottante sont retournées dans s0/d0/v0 comme il convient.

Pour en-valeur de retour qui ne peut pas être transmis via les registres, l’appelant se réserve un bloc de mémoire de taille suffisante et l’alignement doit contenir le résultat. L’adresse du bloc de mémoire doit être passé en tant qu’argument supplémentaire à la fonction dans x8 pour un type POD ou dans x0 (ou x1 si $ces données sont transmises dans x0) pour le type non POD. L’appelé peut modifier le bloc de mémoire de résultat à tout moment pendant l’exécution de la sous-routine (n’est aucun nécessaire pour l’appelé conserver la valeur stockée dans x8, mais pour non POD, l’adresse de cette mémoire tampon ne doit être également renvoyé dans x0 par l’appelé).

## <a name="stack"></a>Stack

Après l’ABI iaasb par ARM, la pile doit rester 16 octets alignés en permanence. AArch64 contient une fonctionnalité de matériel qui génère l’alignement de pile alignées erreurs chaque fois qu’un magasin ou une charge de service pack relatif est effectuée et la procédure stockée n’est pas 16 octets. Windows s’exécute avec cette fonctionnalité est activée en permanence.

Fonctions qui alloue 4 Ko ou plus intéressant de pile doivent garantir que chaque page précédant la dernière page est touché par ordre, ne garantissant ainsi aucun code peut « sauter » les pages de garde Windows utilise pour développer la pile. En général, cela le `__chkstk` helper, qui a une convention d’appel personnalisée qui transmet l’allocation de pile totale divisée par 16 dans x8.

## <a name="red-zone"></a>Zone rouge

La zone de 16 octets immédiatement sous le pointeur de pile actuel est réservée pour une utilisation par l’analyse et dynamique de scénarios de mise à jour corrective. Cela autorise le code généré avec soin à insérer qui stocke 2 registres au niveau [sp, #-16] et les utilise provisoirement à des fins arbitraires. Le noyau Windows garantit que ces 16 octets ne sera pas remplacées si une exception ou l’interruption est effectuée en mode utilisateur et noyau.

## <a name="kernel-stack"></a>Pile de noyau

La pile de mode noyau par défaut dans Windows est six pages (24 Ko). Apportez une attention aux fonctions avec les mémoires tampons de grande taille de pile en mode noyau. Une interruption mal pourrait intervient avec très peu de marge et créer une vérification d’erreur sur le pile.

## <a name="stack-walking"></a>Parcours de pile

Code au sein de Windows est compilé avec des pointeurs de frame activés ([/Oy-](../build/reference/oy-frame-pointer-omission.md)) pour activer l’exploration de pile rapide. De cela est que x29 (fp) est en général pointe vers le lien suivant dans la chaîne, qui est {fp, lr} paire indiquant le pointeur vers le frame précédent sur la pile et l’adresse de retour. Code tiers est encouragé à activer des pointeurs de frame ainsi afin de permettre le profilage améliorées et le suivi.

## <a name="exception-unwinding"></a>Déroulement d’exception

Déroulement de la gestion des exceptions est assisté via l’utilisation de codes de déroulement. Les codes de déroulement sont une séquence d’octets stockés dans la section .xdata de l’exécutable qui décrivent le fonctionnement du prologue et épilogue de manière abstraite, telles que les effets du prologue d’une fonction peuvent être annulées en préparation de la sauvegarde sur le frame de pile de l’appelant. Pour plus d’informations sur les codes de déroulement, consultez [ARM64 exceptions](arm64-exception-handling.md).

L’interface EABI ARM spécifie également un modèle de déroulement d’exception tire parti des codes de déroulement. Toutefois, la spécification présenté n’est pas suffisante pour le déroulement démarre dans Windows, qui doit gérer les cas où le PC est au milieu du prologue ou un épilogue d’une fonction.

Code qui est généré dynamiquement doit être décrits avec des tables de fonction dynamique via `RtlAddFunctionTable` et les fonctions associées, afin que le code généré peut participer à la gestion des exceptions.

## <a name="cycle-counter"></a>Compteur de cycles

Toutes les UC ARMv8 sont nécessaires pour prendre en charge d’un cycle de Registre du compteur. Il s’agit d’un Registre 64 bits de Windows configure pour être lisibles à n’importe quel niveau de l’exception (y compris en mode mono-utilisateur). Il est accessible via la PMCCNTR_EL0 spécial inscrire, à l’aide de l’opcode MSR dans le code de l’assembly, ou le `_ReadStatusReg` intrinsèque dans le code C/C++.

Notez que le compteur de cycles est un vrai compteur de cycles, pas une horloge de mur et par conséquent, la fréquence de comptage varie selon la fréquence du processeur. Si vous pensez que vous devez connaître la fréquence du compteur de cycle, vous ne devez pas utiliser le compteur de cycles. Au lieu de cela, vous souhaitez mesurer le temps horloge, pour lesquelles vous devez utiliser `QueryPerformanceCounter`.

## <a name="see-also"></a>Voir aussi

[Problèmes courants de migration ARM Visual C++](../build/common-visual-cpp-arm-migration-issues.md)<br/>
[La gestion des exceptions ARM64](../build/arm64-exception-handling.md)
