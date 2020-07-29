---
title: Robustesse
ms.date: 11/04/2016
helpviewer_keywords:
- robustness [CRT]
ms.assetid: 7f1a87f8-eff9-4b76-ae9b-d133d3de6adf
ms.openlocfilehash: 9de2611e29f5f9bfd08839517e873c3dda225af0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211591"
---
# <a name="robustness"></a>Robustesse

Les fonctions suivantes de la bibliothèque Runtime C permettent d'améliorer la robustesse de votre programme.

## <a name="run-time-robustness-functions"></a>Fonctions de robustesse à l'exécution

|Fonction|Utilisation|
|--------------|---------|
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|Transfère le contrôle à votre mécanisme de gestion des erreurs si l' **`new`** opérateur ne parvient pas à allouer de la mémoire.|
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Gère les exceptions Win32 (exceptions structurées par C) en tant qu'exceptions typées C++.|
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|Installe votre propre fonction d’arrêt qui doit être appelée par [terminate](../c-runtime-library/reference/terminate-crt.md).|
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|Installe votre propre fonction d’arrêt qui doit être appelée par [unexpected](../c-runtime-library/reference/unexpected-crt.md).|

## <a name="see-also"></a>Voir aussi

[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[SetUnhandledExceptionFilter](/windows/win32/api/errhandlingapi/nf-errhandlingapi-setunhandledexceptionfilter)<br/>
