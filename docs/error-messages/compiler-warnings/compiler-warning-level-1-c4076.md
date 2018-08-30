---
title: Compilateur avertissement (niveau 1) C4076 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4076
dev_langs:
- C++
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 928b0a78c09773e334c1a291877b74304dab66ec
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198476"
---
# <a name="compiler-warning-level-1-c4076"></a>Avertissement du compilateur (niveau 1) C4076

> «*modificateur de type*' : ne peut pas être utilisé avec le type '*typename*»

## <a name="remarks"></a>Notes

Un modificateur de type, s’il s’agit **signé** ou **non signé**, ne peut pas être utilisé avec un type non entier. *modificateur de type* est ignoré.
  
## <a name="example"></a>Exemple  

L’exemple suivant génère l’avertissement de C4076 ; Pour corriger ce problème, supprimez le **non signé** modificateur de type :

```cpp
// C4076.cpp  
// compile with: /W1 /LD  
unsigned double x;   // C4076  
```