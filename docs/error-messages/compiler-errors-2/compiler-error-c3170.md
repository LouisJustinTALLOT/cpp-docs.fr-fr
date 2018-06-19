---
title: Erreur du compilateur C3170 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3170
dev_langs:
- C++
helpviewer_keywords:
- C3170
ms.assetid: ca9a59d6-7df3-42f0-b028-c09d0af3ac2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8bb077bcad95de0be17e630803b5d4ea9825be61
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33255911"
---
# <a name="compiler-error-c3170"></a>Erreur du compilateur C3170
ne peut pas avoir des identificateurs de module différents dans un projet  
  
 [module](../../windows/module-cpp.md) attributs avec des noms différents ont été trouvés dans deux des fichiers d’une compilation. Un seul `module` attribut peut être spécifié par compilation.  
  
 Identiques `module` attributs peuvent être spécifiés dans plusieurs fichiers de code source.  
  
 Par exemple, si les attributs module suivants ont été trouvés :  
  
```  
// C3170.cpp  
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];  
int main() {}  
```  
  
 Puis,  
  
```  
// C3170b.cpp  
// compile with: C3170.cpp  
// C3170 expected  
[ module(name="MyModule1", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];  
```  
  
 le compilateur générerait C3170 (Notez les noms différents).