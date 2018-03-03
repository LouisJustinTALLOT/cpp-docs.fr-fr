---
title: interior_ptr (C + c++ / CLI) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- stdcli::language::interior_ptr
- interior_ptr_cpp
- interior_ptr
dev_langs:
- C++
helpviewer_keywords:
- interior_ptr keyword [C++]
ms.assetid: 25160f74-569e-492d-9e3c-67ece7486baa
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cd3e79306cb97413a833e039b0b333cb85b8e56d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="interiorptr-ccli"></a>interior_ptr (C++/CLI)
Un *pointeur intérieur* déclare un pointeur vers à l’intérieur d’un type référence, mais pas à l’objet lui-même. Un pointeur intérieur peut pointer vers un handle de référence, le type de valeur, le handle du type boxed, le membre d’un type managé, ou à un élément d’un tableau managé.  
  
## <a name="all-runtimes"></a>Tous les runtimes  
 (Aucune remarque pour cette fonctionnalité de langage ne s’applique à tous les runtimes.)  
  
## <a name="windows-runtime"></a>Windows Runtime  
 (Aucune note de cette fonctionnalité de langage ne s’applique qu’au Windows Runtime.)  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime  
 L’exemple de syntaxe suivante illustre un pointeur intérieur.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
cli::interior_ptr<cv_qualifier type> var = &initializer;  
```  
  
### <a name="parameters"></a>Paramètres  
 *cv_qualifier*  
 **const** ou `volatile` qualificateurs.  
  
 *type*  
 Le type de *initialiseur*.  
  
 *var*  
 Le nom de la `interior_ptr` variable.  
  
 *initializer*  
 Un membre d’un type référence, un élément d’un tableau managé ou tout autre objet que vous pouvez affecter à un pointeur natif.  
  
### <a name="remarks"></a>Notes  
 Un pointeur natif n’est pas en mesure de suivre un élément en tant que les modifications apportées à son emplacement sur le tas managé, ce qui entraîne le déplacement des instances d’un objet de garbage collector. Pour un pointeur vers correctement référence à l’instance, le runtime doit mettre à jour le pointeur à l’objet qui vient d’être positionnée.  
  
 Un `interior_ptr` représente un sur-ensemble de la fonctionnalité d’un pointeur natif.  Par conséquent, tout ce qui peut être assigné à un pointeur natif peut également être affecté à un `interior_ptr`.  Un pointeur intérieur est autorisé à effectuer le même jeu d’opérations que les pointeurs natifs, y compris la comparaison et l’opération arithmétique de pointeur.  
  
 Un pointeur intérieur peut uniquement être déclaré sur la pile.  Un pointeur intérieur ne peut pas être déclaré en tant que membre d’une classe.  
  
 Dans la mesure où il existe des pointeurs intérieurs uniquement sur la pile, prise d’adresse d’un pointeur intérieur génère un pointeur non managé.  
  
 `interior_ptr`a une conversion implicite vers `bool`, ce qui permet de son utilisation dans des instructions conditionnelles.  
  
 Pour plus d’informations sur la façon de déclarer un pointeur intérieur qui pointe vers un objet qui ne peut pas être déplacé sur le tas de garbage collection, consultez [pin_ptr](../windows/pin-ptr-cpp-cli.md).  
  
 `interior_ptr` est dans l'espace de noms cli.  Consultez [plateforme, par défaut et espaces de noms cli](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md) pour plus d’informations.  
  
 Pour plus d’informations sur les pointeurs intérieurs, consultez  
  
-   [Guide pratique pour déclarer et utiliser des pointeurs intérieurs et des tableaux managés (C++-CLI)](../windows/how-to-declare-and-use-interior-pointers-and-managed-arrays-cpp-cli.md)  
  
-   [Guide pratique pour déclarer des types de valeur avec le mot clé interior_ptr (C++-CLI)](../windows/how-to-declare-value-types-with-the-interior-ptr-keyword-cpp-cli.md)  
  
-   [Guide pratique pour surcharger des fonctions avec des pointeurs intérieurs et des pointeurs natifs (C++-CLI)](../windows/how-to-overload-functions-with-interior-pointers-and-native-pointers-cpp-cli.md)  
  
-   [Guide pratique pour déclarer des pointeurs intérieurs avec le mot clé const (C++-CLI)](../windows/how-to-declare-interior-pointers-with-the-const-keyword-cpp-cli.md)  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/clr**  
  
### <a name="examples"></a>Exemples  
 **Exemple**  
  
 L’exemple suivant montre comment déclarer et utiliser un pointeur intérieur en un type référence.  
  
```cpp  
// interior_ptr.cpp  
// compile with: /clr  
using namespace System;  
  
ref class MyClass {  
public:  
   int data;  
};  
  
int main() {  
   MyClass ^ h_MyClass = gcnew MyClass;  
   h_MyClass->data = 1;  
   Console::WriteLine(h_MyClass->data);  
  
   interior_ptr<int> p = &(h_MyClass->data);  
   *p = 2;  
   Console::WriteLine(h_MyClass->data);  
  
   // alternatively  
   interior_ptr<MyClass ^> p2 = &h_MyClass;  
   (*p2)->data = 3;  
   Console::WriteLine((*p2)->data);  
}  
```  
  
 **Sortie**  
  
```Output  
1  
2  
3  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)