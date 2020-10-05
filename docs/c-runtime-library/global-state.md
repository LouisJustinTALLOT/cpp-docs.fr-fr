---
title: État global dans le CRT
description: Décrit comment un état global partagé est géré dans le runtime Microsoft Universal C.
ms.topic: conceptual
ms.date: 10/02/2020
helpviewer_keywords:
- CRT global state
ms.openlocfilehash: 6c8b97e2bd6fa71891aedacb1fbfec2bbe382d84
ms.sourcegitcommit: faedcc3be78b29c78e5d51e3c7c7c2f448c745bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91717513"
---
# <a name="global-state-in-the-crt"></a>État global dans le CRT

Certaines fonctions du runtime C universel (UCRT) utilisent l’état global. Par exemple, `setlocale()` définit les paramètres régionaux pour le programme entier, ce qui affecte les séparateurs de chiffres, la page de codes texte, etc.

L’état global de UCRT n’est pas partagé entre les applications et le système d’exploitation. Par exemple, si votre application appelle `setlocale()` , elle n’affecte pas les paramètres régionaux pour tous les composants du système d’exploitation qui utilisent le runtime C, ou l’inverse.

## <a name="os-specific-versions-of-crt-functions"></a>Versions spécifiques au système d’exploitation des fonctions CRT

Dans le UCRT, les fonctions qui interagissent avec l’état global ont une fonction « double », précédée de `_o_` . Par exemple :

- `setlocale()` affecte l’état global propre à l’application.
- `_o_setlocale()` affecte l’état global partagé par tous les composants du système d’exploitation, mais pas pour les applications.

La seule différence entre ces fonctions de « représentation » réside dans le fait que lorsqu’ils lisent/écrivent l’état du CRT global, les versions spécifiques du système d’exploitation (autrement dit, les versions qui commencent par `_o_` ) utilisent la copie du système d’exploitation de l’état global au lieu de la copie de l’état global de l’application.

Les versions spécifiques au système d’exploitation de ces fonctions se trouvent dans `ucrt.osmode.lib` . Par exemple, la version spécifique du système d’exploitation de `setlocale()` est `_o_setlocale()`

Il existe deux façons d’isoler l’état du CRT de votre composant de l’État CRT d’une application :

- Liez de manière statique votre composant à l’aide des options du compilateur `/MT` (version finale) ou `/MTd` (débogage). Pour plus d’informations, consultez [/MD,/MT,/LD](../build/reference/md-mt-ld-use-run-time-library.md). La liaison statique peut augmenter de façon considérable la taille binaire.
- À compter de Windows 10 version 2004, établir une liaison dynamique au CRT, mais appeler les exportations en mode système d’exploitation (les fonctions qui commencent par _o_). Pour appeler les exportations en mode système d’exploitation, liez statiquement comme avant, mais ignorez le UCRT statique à l’aide de l’option de l’éditeur de liens `/NODEFAULTLIB:libucrt.lib` (Release) ou `/NODEFAULTLIB:libucrtd.lib` (Debug). Et ajoutez `ucrt.osmode.lib` à l’entrée de l’éditeur de liens. Pour plus d’informations [, consultez/NODEFAULTLIB (ignorer les bibliothèques)](../build/reference/nodefaultlib-ignore-libraries.md) .

> [!Note]
> Dans le code source, écrivez `setlocale()` , et non `_o_setlocale()` . Lorsque vous vous liez à `ucrt.osmode.lib` , l’éditeur de liens remplace automatiquement la version propre au système d’exploitation de la fonction. Autrement dit, `setlocale()` sera remplacé par `_o_setlocale()` .

La liaison par rapport à `ucrt.osmode.lib` désactive certains appels UCRT qui sont uniquement disponibles en mode application. Toute tentative d’appel à ces erreurs entraîne une erreur de liaison.

## <a name="global-state-affected-by-appos-separation"></a>État global affecté par la séparation de l’application/du système d’exploitation

L’état global affecté par la séparation de l’état de l’application et du système d’exploitation comprend :

- [Données des paramètres régionaux](locale.md)
- Gestionnaires de signal définis par [signal](reference/signal.md)
- Routines d’arrêt définies par [Terminate](reference/set-terminate-crt.md)
- [errno et _doserrno](errno-doserrno-sys-errlist-and-sys-nerr.md)
- État de génération de nombres aléatoires utilisé par [Rand](reference/rand.md) et [srand](reference/srand.md)
- Fonctions qui retournent une mémoire tampon que l’utilisateur n’a pas besoin de libérer : [strtok, wcstok, _mbstok](reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) [tmpnam, _wtmpnam](reference/tempnam-wtempnam-tmpnam-wtmpnam.md) [asctime, _wasctime](reference/asctime-wasctime.md) [gmtime, _gmtime32, _gmtime64](reference/gmtime-gmtime32-gmtime64.md) [_fcvt](reference/fcvt.md) [_ecvt](reference/ecvt.md) [strerror, _strerror, _wcserror,](reference/strerror-strerror-wcserror-wcserror.md) __wcserror
- Mémoire tampon utilisée par [_putch, _putwch](reference/putch-putwch.md)
- [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)
- [_set_new_handler](reference/set-new-handler.md) et [_set_new_mode](reference/set-new-mode.md)
- [fmode](text-and-binary-mode-file-i-o.md)
- [Informations de fuseau horaire](time-management.md)

## <a name="see-also"></a>Voir aussi

[Référence de la bibliothèque Runtime C](c-run-time-library-reference.md)
