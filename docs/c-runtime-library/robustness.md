---
title: Robustesse
ms.date: 11/04/2016
f1_keywords:
- c.runtime
helpviewer_keywords:
- robustness [CRT]
ms.assetid: 7f1a87f8-eff9-4b76-ae9b-d133d3de6adf
ms.openlocfilehash: f41fc019c6a1779362644e29c5518d40690fe9db
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500669"
---
# <a name="robustness"></a>Robustesse

Les fonctions suivantes de la bibliothèque Runtime C permettent d'améliorer la robustesse de votre programme.

## <a name="run-time-robustness-functions"></a>Fonctions de robustesse à l'exécution

|Fonction|Utilisez|
|--------------|---------|
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|Transfère le contrôle à votre mécanisme de gestion des erreurs si l’opérateur **new** ne peut pas allouer de mémoire.|
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Gère les exceptions Win32 (exceptions structurées par C) en tant qu'exceptions typées C++.|
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|Installe votre propre fonction d’arrêt qui doit être appelée par [terminate](../c-runtime-library/reference/terminate-crt.md).|
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|Installe votre propre fonction d’arrêt qui doit être appelée par [unexpected](../c-runtime-library/reference/unexpected-crt.md).|

## <a name="see-also"></a>Voir aussi

[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[SetUnhandledExceptionFilter](/win32/api/errhandlingapi/nf-errhandlingapi-setunhandledexceptionfilter)<br/>
