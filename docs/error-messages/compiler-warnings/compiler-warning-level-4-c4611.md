---
title: Compilateur avertissement (niveau 4) C4611 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4611
dev_langs:
- C++
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5946c10b5e0e0e7e08f1ee37c77120896937adb1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293151"
---
# <a name="compiler-warning-level-4-c4611"></a>Avertissement du compilateur (niveau 4) C4611
interaction entre 'fonction' et la destruction d’objets C++ n’est pas portable  
  
 Sur certaines plateformes, les fonctions qui incluent **catch** peut prend pas en charge la sémantique de destruction lorsque hors de portée d’objet C++.  
  
 Pour éviter un comportement inattendu, évitez d’utiliser **catch** dans les fonctions qui possèdent des constructeurs et destructeurs.  
  
 Cet avertissement est émis uniquement une seule fois ; consultez [(pragma) warning](../../preprocessor/warning.md).