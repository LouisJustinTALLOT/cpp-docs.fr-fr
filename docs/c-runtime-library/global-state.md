---
title: État global dans le CRT
description: Décrit comment un état global partagé est géré dans le runtime Microsoft Universal C.
ms.topic: conceptual
ms.date: 04/02/2020
helpviewer_keywords:
- CRT global state
ms.openlocfilehash: 60532fbdb905bd8ea78b4ce705ec8ecc3e374d9d
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589729"
---
# <a name="global-state-in-the-crt"></a>État global dans le CRT

Certaines fonctions du runtime C universel (UCRT) utilisent l’état global. Par exemple, `setlocale()` définit les paramètres régionaux pour le programme entier, ce qui affecte les séparateurs de chiffres, la page de codes texte, etc.

L’état global de UCRT n’est pas partagé entre les applications et le système d’exploitation. Par exemple, si votre application appelle `setlocale()` , elle n’affecte pas les paramètres régionaux pour les composants du système d’exploitation qui utilisent le runtime C, ou vice versa.

## <a name="os-specific-versions-of-crt-functions"></a>Versions spécifiques au système d’exploitation des fonctions CRT

Dans le UCRT, les fonctions qui interagissent avec l’état global ont une fonction « double », précédée de `_o_` . Par exemple :

- `setlocale()` affecte l’état global propre à l’application.
- `_o_setlocale()` affecte l’état global partagé par tous les composants du système d’exploitation, mais pas pour les applications.

La seule différence entre ces fonctions de « représentation » réside dans le fait que lorsqu’ils lisent/écrivent l’état du CRT global, les versions spécifiques du système d’exploitation (autrement dit, les versions qui commencent par `_o_` ) utilisent la copie du système d’exploitation de l’état global au lieu de la copie de l’état global de l’application.

Les versions spécifiques au système d’exploitation de ces fonctions se trouvent dans `ucrt.osmode.lib` . Par exemple, la version spécifique du système d’exploitation de `setlocale()` est `_o_setlocale()`

Il existe deux façons d’isoler l’état du CRT de votre composant de l’État CRT d’une application :

- Liez de manière statique votre composant à l’aide des options du compilateur/MT (Release) ou MTd (Debug). Pour plus d’informations, consultez [/MD,/MT,/LD](../build/reference/md-mt-ld-use-run-time-library.md). Notez que la liaison statique peut augmenter de façon considérable la taille binaire.
- À compter de Windows 10 20H2, récupérez l’isolation d’État CRT en établissant une liaison dynamique au CRT, mais appelez les exportations en mode système d’exploitation (les fonctions qui commencent par _o_). Pour appeler les exportations en mode système d’exploitation, liez statiquement comme avant, mais ignorez le UCRT statique à l’aide de l’option de l’éditeur de liens `/NODEFAULTLIB:libucrt.lib` (version) ou `/NODEFAULTLIB:libucrtd.lib` (débogage) consultez [/NODEFAULTLIB (ignorer les bibliothèques)](../build/reference/nodefaultlib-ignore-libraries.md) pour plus d’informations. Et ajoutez `ucrt.osmode.lib` à l’entrée de l’éditeur de liens.

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
- [fmode] (text-and-binary-mode-file-i-o.md)
- [Informations de fuseau horaire](time-management.md)

## <a name="see-also"></a>Voir aussi

[Référence de la bibliothèque Runtime C](c-run-time-library-reference.md)
