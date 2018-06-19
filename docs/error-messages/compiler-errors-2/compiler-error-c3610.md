---
title: Erreur du compilateur C3610 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3610
dev_langs:
- C++
helpviewer_keywords:
- C3610
ms.assetid: 9349a348-9d37-4a00-9eab-481039268d31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f58d66e9d3dacfa2c0b38eb84fe51e0813a892d3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252430"
---
# <a name="compiler-error-c3610"></a>Erreur du compilateur C3610
'valuetype' : type de valeur doit être 'boxed' avant l’appel de méthode 'méthode'  
  
 Par défaut, un type valeur n’est pas sur le tas managé. Avant que vous pouvez appeler les méthodes de classes de runtime .NET, tel que `Object`, vous devez déplacer le type de valeur dans le tas managé.  
  
 C3610 est uniquement accessible à l’aide de l’option du compilateur obsolète **oldSyntax ;**.  
