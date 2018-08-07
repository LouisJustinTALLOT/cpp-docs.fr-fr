---
title: Génériques et modèles (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- generics [C++], vs. templates
- templates, C++
ms.assetid: 63adec79-b1dc-4a1a-a21d-b8a72a8fce31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3ebb476b0a8c384759c9d44101e7bac7083103b2
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570764"
---
# <a name="generics-and-templates-visual-c"></a>Génériques et modèles (Visual C++)
Génériques et les modèles sont des fonctionnalités de langage qui prennent en charge des types paramétrables. Cependant, ils sont différents et des utilisations différentes. Cette rubrique fournit une vue d’ensemble des nombreuses différences.  
  
 Pour plus d’informations, consultez [Windows Runtime et modèles gérés](../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md).  
  
## <a name="comparing-templates-and-generics"></a>Comparaison des modèles et génériques  
 Principales différences entre les modèles C++ et les génériques :  
  
-   Les génériques sont génériques jusqu'à ce que les types sont substitués pour eux lors de l’exécution. Les modèles sont spécialisés au moment de la compilation afin qu’ils ne soient pas des types paramétrables toujours lors de l’exécution  
  
-   Le common language runtime prend spécifiquement en charge les génériques dans le langage MSIL. Étant donné que le runtime sait à propos des génériques, des types spécifiques peuvent être remplacés pour les types génériques lors du référencement d’un assembly contenant un type générique. En revanche, résoudre les modèles, en types ordinaires au moment de la compilation et les types qui en résulte ne peuvent pas être spécialisés dans d’autres assemblys.  
  
-   Les génériques spécialisée dans les deux assemblys différents avec le même type arguments sont du même type. Modèles spécialisés dans les deux assemblys différents avec le même type arguments sont considérés comme par le runtime différents types.  
  
-   Les génériques sont générées sous la forme d’un seul élément de code exécutable qui est utilisé pour tous les arguments de type référence (cela n’est pas vrai pour les types valeur, qui ont une implémentation unique par type de valeur). Le compilateur JIT sait à propos des génériques et est en mesure d’optimiser le code pour les types référence ou valeur qui sont utilisés comme arguments de type. Modèles génèrent du code d’exécution distinct pour chaque spécialisation.  
  
-   Génériques n’autorisent pas les paramètres de modèle sans type, tel que `template <int i> C {}`. Modèles de les autoriser.  
  
-   Les génériques ne permettent pas de spécialisation explicite (autrement dit, une implémentation personnalisée d’un modèle pour un type spécifique). Modèles de le faire.  
  
-   Les génériques ne permettent pas de spécialisation partielle (une implémentation personnalisée pour un sous-ensemble des arguments de type). Modèles de le faire.  
  
-   Les génériques n’autorisent pas le paramètre de type à utiliser comme classe de base pour le type générique. Modèles de le faire.  
  
-   Modèles prennent en charge les paramètres de modèle de modèle (par exemple, `template<template<class T> class X> class MyClass`), mais n’est pas le cas de génériques.  
  
## <a name="combining-templates-and-generics"></a>Combinaison de modèles et génériques  
  
-   La principale différence dans les génériques a des implications en matière de création d’applications qui combinent des modèles et les génériques. Par exemple, supposons que vous avez une classe de modèle que vous souhaitez créer un wrapper générique pour exposer ce modèle dans d’autres langages comme générique. Vous ne pouvez avoir le générique prennent un paramètre de type qu’il transmet ensuite directement vers le modèle, dans la mesure où le modèle a besoin d’avoir ce paramètre de type au moment de la compilation, mais le générique ne résout pas le paramètre de type avant l’exécution. Imbrication d’un modèle à l’intérieur d’un générique ne fonctionnera, car il n’existe aucun moyen pour développer les modèles au moment de la compilation pour les types génériques arbitraires qui peut être instancié lors de l’exécution.  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L’exemple suivant montre un exemple simple de l’utilisation conjointe de modèles et les génériques. Dans cet exemple, la classe de modèle transmet son paramètre via au type générique. L’inverse n’est pas possible.  
  
 Cet idiome pourrait être utilisé lorsque vous voulez créer sur une API générique existante avec le code du modèle qui est local à un assembly Visual C++, ou lorsque vous avez besoin ajouter une couche supplémentaire de paramétrage à un type générique, pour tirer parti de certaines fonctionnalités des modèles non prises en charge d par génériques.  
  
### <a name="code"></a>Code  
  
```cpp  
// templates_and_generics.cpp  
// compile with: /clr  
using namespace System;  
  
generic <class ItemType>  
ref class MyGeneric {  
   ItemType m_item;  
  
public:  
   MyGeneric(ItemType item) : m_item(item) {}  
   void F() {   
      Console::WriteLine("F");   
   }  
};  
  
template <class T>  
public ref class MyRef {  
MyGeneric<T>^ ig;  
  
public:  
   MyRef(T t) {  
      ig = gcnew MyGeneric<T>(t);  
      ig->F();  
    }      
};  
  
int main() {  
   // instantiate the template  
   MyRef<int>^ mref = gcnew MyRef<int>(11);  
}  
```  
  
### <a name="output"></a>Sortie  
  
```Output  
F  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Génériques](../windows/generics-cpp-component-extensions.md)