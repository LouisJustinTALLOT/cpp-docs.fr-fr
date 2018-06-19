---
title: Sceller une fonction virtuelle | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sealed keyword [C++]
- derived classes, virtual functions
- virtual functions, sealing
- __sealed keyword
ms.assetid: 0e9fae03-6425-4512-9a24-8ccb6dc8a0d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c85f4775025d3661fdfbf8967b310fb733f452b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33164594"
---
# <a name="sealing-a-virtual-function"></a>Sceller une fonction virtuelle
La syntaxe pour sceller une fonction virtuelle a changé entre les Extensions managées pour C++ vers Visual C++.  
  
 Le `__sealed` mot clé est utilisé dans les Extensions managées pour modifier un type référence, interdire les dérivations suivantes (voir [déclaration d’un Type de classe gérée](../dotnet/declaration-of-a-managed-class-type.md)), ou pour modifier une fonction virtuelle, en interdisant substitution suivante de la méthode dans une classe dérivée. Par exemple :  
  
```  
__gc class base { public: virtual void f(); };  
__gc class derived : public base {  
public:  
   __sealed void f();  
};  
```  
  
 Dans cet exemple, `derived::f()` remplace le `base::f()` basé sur une instance de la correspondance exacte du prototype de fonction. Le `__sealed` mot clé indique qu’une classe suivante héritée de la classe dérivée ne peut pas fournir une substitution de `derived::f()`.  
  
 Dans la nouvelle syntaxe, `sealed` est placé après la signature plutôt que d’être autorisé à apparaître avant le prototype de fonction réelle, comme il a été précédemment autorisé. En outre, l’utilisation de `sealed` requiert l’utilisation explicite de le `virtual` mot clé. Autrement dit, la traduction de `derived`ci-dessus, est la suivante :  
  
```  
ref class derived: public base {  
public:  
   virtual void f() override sealed;  
};  
```  
  
 L’absence de le `virtual` mot clé dans cette instance entraîne une erreur. Dans la nouvelle syntaxe, le mot clé contextuel `abstract` peut être utilisé à la place de la `=0` pour indiquer une fonction virtuelle pure. Cela n’était pas pris en charge dans les Extensions managées. Par exemple :  
  
```  
__gc class base { public: virtual void f()=0; };  
```  
  
 peut être réécrite sous la forme  
  
```  
ref class base { public: virtual void f() abstract; };  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Déclarations de membre dans une classe ou Interface (C + c++ / CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [sealed](../windows/sealed-cpp-component-extensions.md)