---
title: Erreur du compilateur C3382 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3382
dev_langs:
- C++
helpviewer_keywords:
- C3382
ms.assetid: a7603abd-ac4e-4ae6-a02b-3bdc6d1908a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8bcca58aecc3d5a5e7b621f45e102690c9f138c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33254535"
---
# <a name="compiler-error-c3382"></a>Erreur du compilateur C3382
'sizeof' n'est pas pris en charge avec /clr:safe  
  
 Le fichier de sortie d’une compilation **/clr:safe** est un fichier de type sécurisé vérifiable. De plus, sizeof n’est pas pris en charge, car la valeur de retour de l’opérateur sizeof est size_t, dont la taille varie selon le système d’exploitation.  
  
 Pour plus d'informations, consultez  
  
-   [sizeof, opérateur](../../cpp/sizeof-operator.md)  
  
-   [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Problèmes courants de migration vers Visual C++ 64 bits](../../build/common-visual-cpp-64-bit-migration-issues.md)  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C3382 :  
  
```  
// C3382.cpp  
// compile with: /clr:safe  
int main() {  
   sizeof( char );   // C3382  
}  
```