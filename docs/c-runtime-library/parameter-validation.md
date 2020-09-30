---
title: Validation des paramètres
description: Description de la validation des paramètres dans la bibliothèque Runtime C de Microsoft.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parameters, validation
ms.assetid: 019dd5f0-dc61-4d2e-b4e9-b66409ddf1f2
ms.openlocfilehash: 60ded7fc5a4388b2c4bf87ab5a388caab5fc47c2
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589820"
---
# <a name="parameter-validation"></a>Validation des paramètres

La plupart des fonctions CRT à sécurité améliorée, et beaucoup qui ne le sont pas, valident leurs paramètres pour des opérations telles que la vérification des pointeurs pour la **valeur null**, que les entiers entrent dans une plage valide ou que les valeurs d’énumération sont valides. Si un paramètre non valide est trouvé, le gestionnaire de paramètre non valide est appelé.

## <a name="invalid-parameter-handler-routine"></a>Routine du gestionnaire du paramètre non valide

Quand une fonction de la bibliothèque Runtime C détecte un paramètre non valide, elle capture des informations sur l’erreur, puis appelle une macro qui encapsule une fonction de distribution du gestionnaire de paramètres non valide. Qui sera l’une des [_invalid_parameter](../c-runtime-library/reference/invalid-parameter-functions.md), [_invalid_parameter_noinfo](../c-runtime-library/reference/invalid-parameter-functions.md)ou [_invalid_parameter_noinfo_noreturn](../c-runtime-library/reference/invalid-parameter-functions.md). La fonction de distribution appelée varie selon que votre code est, respectivement, une version de débogage, une version commerciale ou si l’erreur n’est pas considérée comme récupérable.

Dans les versions Debug, la macro de paramètre non valide déclenche généralement une assertion ayant échoué et un point d’arrêt du débogueur avant l’appel de la fonction Dispatch. Lorsque le code est exécuté, l’assertion peut être signalée à l’utilisateur dans une boîte de dialogue avec les options « abandonner », « Réessayer » et « continuer », ou des choix similaires en fonction de la version du système d’exploitation et de la bibliothèque Runtime. Ces options permettent à l’utilisateur de terminer immédiatement le programme, d’attacher un débogueur ou de laisser le code existant continuer à s’exécuter, ce qui appelle la fonction de distribution.

La fonction de distribution du gestionnaire de paramètre non valide appelle le gestionnaire de paramètre non valide actuellement assigné. Par défaut, le paramètre non valide appelle `_invoke_watson` , ce qui entraîne la fermeture de l’application et la génération d’un mini-vidage. S’il est activé par le système d’exploitation, une boîte de dialogue demande à l’utilisateur s’il souhaite envoyer le vidage sur incident à Microsoft pour analyse.

Vous pouvez modifier ce comportement à l’aide des fonctions [_set_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) ou [_set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) pour définir le gestionnaire de paramètres non valides sur votre propre fonction. Si la fonction que vous spécifiez n’arrête pas l’application, le contrôle est retourné à la fonction qui a reçu les paramètres non valides. Dans le CRT, ces fonctions arrêtent normalement l’exécution de la fonction, définissent `errno` à un code d’erreur et retournent un code d’erreur. Dans de nombreux cas, la `errno` valeur et la valeur de retour sont toutes les deux `EINVAL` , pour indiquer un paramètre non valide. Dans certains cas, un code d’erreur plus spécifique est retourné, tel que `EBADF` pour un pointeur de fichier incorrect passé en tant que paramètre. 

Pour plus d’informations sur `errno`, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="see-also"></a>Voir aussi

[Fonctionnalités de sécurité dans le CRT](../c-runtime-library/security-features-in-the-crt.md)\
[Fonctionnalités de la bibliothèque CRT](../c-runtime-library/crt-library-features.md)
