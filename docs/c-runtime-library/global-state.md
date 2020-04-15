---
title: État mondial dans la CRT
ms.date: 04/02/2020
helpviewer_keywords:
- CRT global state
ms.openlocfilehash: 487418da104b2edbc45b5d3a664e4385394ada31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81379099"
---
# <a name="global-state-in-the-crt"></a>État mondial dans la CRT

Certaines fonctions de l’Universal C Runtime (UCRT) utilisent l’état mondial. Par exemple, `setlocale()` définit le local pour l’ensemble du programme, qui affecte les séparateurs de chiffres, la page de code de texte, et ainsi de suite.

L’état mondial de l’UCRT n’est pas partagé entre les applications et le système d’exploitation. Par exemple, si `setlocale()`votre application appelle, elle n’affectera pas le lieu pour les composants OS qui utilise le temps d’exécution C, ou vice-versa.

## <a name="os-specific-versions-of-crt-functions"></a>Versions spécifiques à l’OS des fonctions CRT

Dans l’UCRT, les fonctions qui interagissent avec l’État `_o_`mondial ont une fonction « jumelle », préfixée avec . Par exemple :

    `setlocale()` affects global state specific to the app.
    `_o_setlocale()` affects global state shared by all OS components, but not apps.

La seule différence entre ces fonctions "jumelles" est que lorsqu’ils lisent/écrivent l’état global CRT, les versions spécifiques à l’OS (c’est-à-dire les versions qui commencent par `_o_`) utilisent la copie OS de l’état global au lieu de la copie de l’application de l’état mondial.

Les versions spécifiques à l’OS `ucrt.osmode.lib`de ces fonctions sont en . Par exemple, la version spécifique `setlocale()` à l’OS de`_o_setlocale()`

Il existe deux façons d’isoler l’état CRT de votre composant de l’état CRT d’une application :

- Lien statiquez votre composant en utilisant des options de compilateur /MT (libération) ou MTd (debug). Pour plus de détails, voir [/MD, /MT, /LD](https://docs.microsoft.com/cpp/build/reference/md-mt-ld-use-run-time-library?view=vs-2019). Notez que la liaison statique peut augmenter considérablement la taille binaire.
- En commençant par Windows 10 20H2, obtenir l’isolement de l’état CRT en reliant dynamiquement à la CRT, mais appelez les exportations de mode OS (les fonctions qui commencent par _o_). Pour appeler les exportations de mode OS, lien statique comme avant, `/NODEFAULTLIB:libucrt.lib` mais ignorer `/NODEFAULTLIB:libucrtd.lib` l’UCRT statique en utilisant l’option de liaison (libération) ou (debug) Voir [/NODEFAULTLIB (Ignorer les bibliothèques)](https://docs.microsoft.com/cpp/build/reference/nodefaultlib-ignore-libraries?view=vs-2019) pour plus de détails. Et `ucrt.osmode.lib` ajouter à l’entrée linker.

> [!Note]
> Dans le code `setlocale()`source, écrire , pas `_o_setlocale()`. Lorsque vous `ucrt.osmode.lib`liez contre, le lien remplacera automatiquement la version spécifique à l’OS de la fonction. `setlocale()` C’est-à-dire, `_o_setlocale()`sera remplacé par .

Liaison `ucrt.osmode.lib` contre les désactiver certains appels UCRT qui ne sont disponibles qu’en mode application. Tenter de les appeler entraînera une erreur de lien.

## <a name="global-state-affected-by-appos-separation"></a>État mondial affecté par la séparation app/OS

L’état mondial affecté par la séparation de l’application et de l’état d’OS comprend :

- [Données locales](locale.md)
- Gestionnaires de signaux réglés par [signal](reference/signal.md)
- Interruptions de résiliation réglées par [fin](reference/set-terminate-crt.md)
- [errno et _doserrno](errno-doserrno-sys-errlist-and-sys-nerr.md)
- État aléatoire de génération de nombres utilisé par [rand](reference/rand.md) et [srand](reference/srand.md)
- Fonctions qui renvoient un tampon que l’utilisateur n’a pas besoin de libérer: [strtok, wcstok, _mbstok](reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) [Tmpnam, _wtmpnam](reference/tempnam-wtempnam-tmpnam-wtmpnam.md) [asctime, _wasctime](reference/asctime-wasctime.md) [gmtime, _gmtime32, _gmtime64](reference/gmtime-gmtime32-gmtime64.md) [_fcvt](reference/fcvt.md) [_ecvt](reference/ecvt.md) [strerror, _strerror, _wcserror, __wcserror](reference/strerror-strerror-wcserror-wcserror.md)
- Le tampon utilisé par [_putch, _putwch](reference/putch-putwch.md)
- [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)
- [_set_new_handler](reference/set-new-handler.md) et [_set_new_mode](reference/set-new-mode.md)
- [fmode] (text-and-binary-mode-file-i-o.md)
- [Informations de fuseau horaire](time-management.md)

## <a name="see-also"></a>Voir aussi

[C Référence de bibliothèque Run-Time](c-run-time-library-reference.md)