---
title: L’erreur C2696 erreur de compilateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2696
dev_langs:
- C++
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65ccdd6d2c8c34c360811b80d5a93abe76f5ef8e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33235037"
---
# <a name="compiler-error-c2696"></a>Erreur C2696 erreur de compilateur
Impossible de créer un objet temporaire d’un type managé 'type'  
  
Des références aux `const` dans un programme non managé que le compilateur appelle le constructeur et créer un objet temporaire sur la pile. Toutefois, une classe managée ne peut jamais être créée sur la pile.  
  
L’erreur C2696 est uniquement accessible à l’aide de l’option du compilateur obsolète **oldSyntax ;**.  
