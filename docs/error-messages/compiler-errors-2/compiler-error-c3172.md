---
title: Erreur du compilateur C3172 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3172
dev_langs:
- C++
helpviewer_keywords:
- C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b3feadd9c8fc39edb707e8dbd3a80ed90d078d72
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33254374"
---
# <a name="compiler-error-c3172"></a>Erreur du compilateur C3172
'nom_module' : Impossible de spécifier des attributs idl_module différents dans un projet  
  
 [idl_module](../../windows/idl-module.md) attributs ayant le même nom mais des `dllname` ou `version` paramètres ont été trouvés dans deux des fichiers d’une compilation. Un seul `idl_module` attribut peut être spécifié par compilation.  
  
 Identiques `idl_module` attributs peuvent être spécifiés dans plusieurs fichiers de code source.  
  
 Par exemple, si les éléments suivants `idl_module` attributs ont été trouvés :  
  
```  
// C3172.cpp  
[module(name="MyMod")];  
[ idl_module(name="x", dllname="file.dll", version="1.1") ];  
int main() {}  
```  
  
 Puis,  
  
```  
// C3172b.cpp  
// compile with: C3172.cpp  
// C3172 expected  
[ idl_module(name="x", dllname="file.dll", version="1.0") ];  
```  
  
 le compilateur génère l’erreur C3172 (Notez les valeurs de version différente).