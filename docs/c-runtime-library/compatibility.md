---
title: Compatibilité
description: Décrit la compatibilité de la bibliothèque Microsoft Universal C Runtime (UCRT) avec la bibliothèque C standard, POSIX, le CRT sécurisé et les applications du Windows Store.
ms.date: 9/11/2020
ms.topic: conceptual
helpviewer_keywords:
- CRT, compatibility
- compatibility, C runtime libraries
- compatibility
ms.assetid: 346709cb-edda-4909-9a19-3d253eddb6b7
ms.openlocfilehash: 10c21f3f471c105ac4e40bda449aaf8987edba25
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590041"
---
# <a name="compatibility"></a>Compatibilité

La bibliothèque Runtime C universel (UCRT) prend en charge la majeure partie de la bibliothèque standard C requise pour la conformité C++. Il implémente la bibliothèque C99 (ISO/IEC 9899:1999), à quelques exceptions près :

- compatibilité de type stricte dans \<complex.h> .
- `aligned_alloc`, qui n’est probablement pas implémenté, car le système d’exploitation Windows ne prend pas en charge les allocations alignées. Utilisez plutôt le non standard `_aligned_malloc` .
- `strerrorlen_s`
- prise en charge atomique dans \<stdatomic.h>
- prise en charge des threads dans \<threads.h>

Le UCRT implémente également un grand sous-ensemble de la bibliothèque POSIX. 1 (ISO/IEC 9945-1:1996, POSIX System Application Program Interface). Toutefois, il n’est pas entièrement conforme à une norme POSIX spécifique. Le UCRT implémente également plusieurs fonctions et macros propres à Microsoft qui ne font pas partie d’une norme.

Les fonctions spécifiques à l’implémentation Microsoft de Visual C++ se trouvent dans la bibliothèque vcruntime.  La plupart de ces fonctions sont destinées à un usage interne et ne peuvent pas être appelées par le code utilisateur. La documentation décrit certaines fonctions destinées au débogage et à l’implémentation de la compatibilité.

La norme C++ réserve à l’implémentation des noms qui commencent par un trait de soulignement dans l’espace de noms global. Les fonctions POSIX et les fonctions de bibliothèque Runtime spécifiques à Microsoft se trouvent dans l’espace de noms global, mais ne font pas partie de la bibliothèque Runtime C standard. C’est la raison pour laquelle les implémentations Microsoft préférées de ces fonctions ont un trait de soulignement de début. Pour des raisons de portabilité, la bibliothèque UCRT prend également en charge les noms par défaut. Toutefois, le compilateur Microsoft C++ émet un avertissement de dépréciation quand du code qui les utilise est compilé. Seuls les noms par défaut sont déconseillés, pas les fonctions elles-mêmes. Pour supprimer l’avertissement, définissez `_CRT_NONSTDC_NO_WARNINGS` avant d’inclure des en-têtes dans le code qui utilise les noms POSIX d’origine.

Certaines fonctions de la bibliothèque C standard ont un historique d’utilisation non sécurisée, en raison de paramètres mal utilisés et de mémoires tampons non vérifiées. Ces fonctions sont souvent à l’origine de problèmes de sécurité dans le code. Microsoft a créé un ensemble de versions plus sécurisées de ces fonctions qui vérifient l’utilisation des paramètres. Ils appellent le gestionnaire de paramètres non valides lorsqu’un problème est détecté au moment de l’exécution.  Par défaut, le compilateur Microsoft C++ émet un avertissement de dépréciation quand une variante plus sécurisée d’une fonction est disponible. Quand vous compilez votre code en C++, vous pouvez définir `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` comme 1 pour éliminer la plupart des avertissements. Cette macro permet aux surcharges de modèle d’appeler les variantes plus sûres tout en conservant le code source portable. Pour supprimer l’avertissement, définissez `_CRT_SECURE_NO_WARNINGS` avant d’inclure des en-têtes dans le code qui utilise ces fonctions. Pour plus d'informations, consultez [Security Features in the CRT](../c-runtime-library/security-features-in-the-crt.md).

À l’exception de ce qui est indiqué dans la documentation pour des fonctions spécifiques, la bibliothèque UCRT est compatible avec l’API Windows.  Certaines fonctions ne sont pas prises en charge dans les applications Windows Store ou plateforme Windows universelle ([UWP](/uwp)). Ces fonctions sont répertoriées dans [fonctions CRT non prises en charge dans les applications plateforme Windows universelle](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="related-articles"></a>Articles connexes

|Titre|Description|
|-----------|-----------------|
|[Applications UWP, Windows Runtime et Runtime C](../c-runtime-library/windows-store-apps-the-windows-runtime-and-the-c-run-time.md)|Décrit le moment où les routines UCRT ne sont pas compatibles avec les applications Windows universelles ou les applications de Microsoft Store.|
|[Conformité ANSI C](../c-runtime-library/ansi-c-compliance.md)|Décrit l’affectation de noms dans la bibliothèque UCRT conforme à la norme.|
|[ENVIRONNEMENTS](../c-runtime-library/unix.md)|Fournit des instructions pour le portage de programmes vers UNIX.|
|[Plateformes Windows (CRT)](../c-runtime-library/windows-platforms-crt.md)|Répertorie les systèmes d'exploitation qui offrent une prise en charge CRT.|
|[Compatibilité descendante](../c-runtime-library/backward-compatibility.md)|Explique comment mapper les anciens noms CRT aux nouveaux.|
|[Fonctionnalités de la bibliothèque CRT](../c-runtime-library/crt-library-features.md)|Offre une vue d'ensemble des fichiers de bibliothèque CRT (.lib) et les options de compilateur associées.|
