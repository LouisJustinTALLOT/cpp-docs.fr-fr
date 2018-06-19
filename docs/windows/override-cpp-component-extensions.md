---
title: Remplacer (Extensions du composant C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- overriding, override keyword [C++]
- override keyword [C++]
ms.assetid: 34d19257-1686-4fcd-96f5-af07c70ba914
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6818256aafc64702e5423a5560c251e6d46750fa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878877"
---
# <a name="override--c-component-extensions"></a>substituer  (extensions du composant C++)
Le `override` mot clé contextuel indique qu’un membre d’un type substitue à une classe de base ou d’un membre d’interface de base.  
  
## <a name="remarks"></a>Notes  
 Le `override` mot clé est valide lors de la compilation pour les cibles natives (option du compilateur de valeur par défaut), les cibles Windows Runtime (**/ZW** option du compilateur), ou les cibles communes du runtime language (**/CLR** compilateur option).  
  
 Pour plus d’informations sur les spécificateurs de substitution, consultez [spécificateur de substitution](../cpp/override-specifier.md) et [des spécificateurs de substitution et Compilations natives](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).  
  
 Pour plus d’informations sur les mots clés contextuels, consultez [mots clés contextuels](../windows/context-sensitive-keywords-cpp-component-extensions.md).  
  
## <a name="examples"></a>Exemples  
 **Exemple**  
  
 L’exemple de code suivant montre que `override` peut également être utilisé dans les compilations natives.  
  
```cpp#  
// override_keyword_1.cpp  
// compile with: /c  
struct I1 {  
   virtual void f();  
};  
  
struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **Exemple**  
  
 L’exemple de code suivant montre que `override` peut être utilisé dans les compilations Windows Runtime.  
  
```cpp#  
// override_keyword_2.cpp  
// compile with: /ZW /c  
ref struct I1 {  
   virtual void f();  
};  
  
ref struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **Spécifications**  
  
 Option du compilateur : **/ZW**  
  
 **Exemple**  
  
 L’exemple de code suivant montre que `override` peut être utilisé dans les compilations de runtime de langage commun.  
  
```cpp#  
// override_keyword_3.cpp  
// compile with: /clr /c  
ref struct I1 {  
   virtual void f();  
};  
  
ref struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **Spécifications**  
  
 Option du compilateur : **/clr**  
  
## <a name="see-also"></a>Voir aussi  
 [Spécificateur de substitution](../cpp/override-specifier.md)   
 [Spécificateurs de substitution](../windows/override-specifiers-cpp-component-extensions.md)