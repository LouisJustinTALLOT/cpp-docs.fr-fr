---
title: Robustesse
ms.date: 11/04/2016
helpviewer_keywords:
- robustness [CRT]
ms.assetid: 7f1a87f8-eff9-4b76-ae9b-d133d3de6adf
ms.openlocfilehash: 5e13152b2c31511cce4df9976d6c800960c099a5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444890"
---
# <a name="robustness"></a>Robustesse

Les fonctions suivantes de la bibliothèque Runtime C permettent d'améliorer la robustesse de votre programme.

## <a name="run-time-robustness-functions"></a>Fonctions de robustesse à l'exécution

|Fonction|Utilisation|
|--------------|---------|
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|Transfère le contrôle à votre mécanisme de gestion des erreurs si l’opérateur **new** ne peut pas allouer de mémoire.|
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Gère les exceptions Win32 (exceptions structurées par C) en tant qu'exceptions typées C++.|
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|Installe votre propre fonction d’arrêt qui doit être appelée par [terminate](../c-runtime-library/reference/terminate-crt.md).|
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|Installe votre propre fonction d’arrêt qui doit être appelée par [unexpected](../c-runtime-library/reference/unexpected-crt.md).|

## <a name="see-also"></a>Voir aussi

[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[SetUnhandledExceptionFilter](/windows/win32/api/errhandlingapi/nf-errhandlingapi-setunhandledexceptionfilter)<br/>
