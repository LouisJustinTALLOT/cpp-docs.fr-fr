---
title: Robustesse | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.runtime
dev_langs:
- C++
helpviewer_keywords:
- robustness [CRT]
ms.assetid: 7f1a87f8-eff9-4b76-ae9b-d133d3de6adf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b76235187bad83eb638588cbbd179e93523fdf2f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409522"
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
 [SetUnhandledExceptionFilter](http://msdn.microsoft.com/library/windows/desktop/ms680634.aspx)<br/>
