---
title: Erreur irrécupérable C1900 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1900
dev_langs:
- C++
helpviewer_keywords:
- C1900
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da7cdd5601785f43748ec87d3219f43728536855
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33228985"
---
# <a name="fatal-error-c1900"></a>Erreur irrécupérable C1900
Incompatibilité IL de 'outil1' version 'numéro1' et 'outil2' version 'numéro2'  
  
 Les outils exécutés dans différentes passes du compilateur ne correspondent pas. ***number1*** et ***number2*** font référence aux dates sur les fichiers. Par exemple, dans la passe 1, le compilateur frontal s'exécute (c1.dll), alors que dans la passe 2, c'est le compilateur principal (c2.dll). Les dates doivent correspondre dans les fichiers.  
  
 Pour résoudre ce problème, assurez-vous que toutes les mises à jour ont été appliquées à Visual Studio. Si le problème persiste, utilisez **programmes et fonctionnalités** dans le panneau de configuration Windows pour réparer ou réinstaller Visual Studio.