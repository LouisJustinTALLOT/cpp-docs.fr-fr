---
title: Erreur du compilateur C3904 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3904
dev_langs:
- C++
helpviewer_keywords:
- C3904
ms.assetid: 08297605-e4f2-4c6c-b637-011f1fd40631
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 86a1d0d51f407069cbed2139322ccc92d5cfeeb6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33271877"
---
# <a name="compiler-error-c3904"></a>Erreur du compilateur C3904
'accesseur_propriété' : doit spécifier ou des paramètres de nombre  
  
 Vérifiez le nombre de paramètres dans votre `get` et `set` méthodes par rapport aux dimensions de la propriété.  
  
-   Le nombre de paramètres pour le `get` (méthode) doit être égal au nombre de dimensions de la propriété ou être égal à zéro pour les propriétés non indexées.  
  
-   Le nombre de paramètres de la `set` (méthode) doit être supérieur au nombre de dimensions de la propriété.  
  
 Pour plus d'informations, consultez [property](../../windows/property-cpp-component-extensions.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C3904.  
  
```  
// C3904.cpp  
// compile with: /clr /c  
ref class X {  
   property int P {  
      // set  
      void set();   // C3904  
      // try the following line instead  
      // void set(int);  
  
      // get  
      int get(int, int);   // C3904  
      // try the following line instead  
      // int get();  
   };  
};  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C3904.  
  
```  
// C3904b.cpp  
// compile with: /clr /c  
ref struct X {  
   property int Q[double, double, float, float, void*, int] {  
      // set  
      void set(double, void*);   // C3904  
      // try the following line instead  
      // void set(double, double, float, float, void*, int, int);  
  
      // get  
      int get();   // C3904  
      // try the following line instead  
      // int get(double, double, float, float, void*, int);  
   }  
};  
```