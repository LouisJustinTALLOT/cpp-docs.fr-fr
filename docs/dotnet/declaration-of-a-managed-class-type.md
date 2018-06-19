---
title: Déclaration d’un Type de classe managée | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __gc types
- classes [C++], managed
- class keyword [C++], CLR
- __value keyword
- value types, declaring
- value keyword [C++]
- managed classes
- interface class keyword
- ref keyword [C++]
ms.assetid: 16de9c94-91d7-492f-8ac7-f0729cc627e9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5c821424d8b2669c78befa604bf2669399c89f75
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33112639"
---
# <a name="declaration-of-a-managed-class-type"></a>Déclaration d'un type de classe managée
La façon de déclarer un type de classe de référence changé entre les Extensions managées pour C++ vers Visual C++.  
  
 Dans les Extensions managées, un type de classe de référence est précédé du `__gc` (mot clé). Dans la nouvelle syntaxe, le `__gc` (mot clé) est remplacé par un des deux mots clés espacés : `ref class` ou `ref struct`. Le choix de `struct` ou `class` indique le public (pour `struct`) ou privé (pour `class`) niveau d’accès par défaut de ses membres déclarés dans une section initiale sans étiquette du corps du type.  
  
 De même, dans les Extensions managées, un type de classe value est précédé du `__value` (mot clé). Dans la nouvelle syntaxe, le `__value` (mot clé) est remplacé par un des deux mots clés espacés : `value class` ou `value struct`.  
  
 Un type interface, dans les Extensions managées, était indiqué par le mot clé `__interface`. Dans la nouvelle syntaxe, il est remplacé par `interface class`.  
  
 Par exemple, les déclarations de classe suivantes dans les Extensions managées :  
  
```  
public __gc class Block {};     // reference class  
public __value class Vector {}; // value class  
public __interface IFooBar {};  // interface class  
```  
  
 Dans la nouvelle syntaxe ces sont déclarées de façon équivalente comme suit :  
  
```  
public ref class Block {};         // reference class  
public value class Vector {};      // value class  
public interface class IFooBar {}; // interface class  
```  
  
## <a name="specifying-the-class-as-abstract"></a>Spécification de la classe comme abstraite  
 Sous les Extensions managées, vous placez le mot clé `__abstract` avant la `class` (mot clé) (avant ou après le `__gc`) pour indiquer que la classe est incomplète et que les objets de la classe ne peut pas être créés dans le programme :  
  
```  
public __gc __abstract class Shape {};  
public __gc __abstract class Shape2D: public Shape {};  
```  
  
 Dans la nouvelle syntaxe, vous spécifiez le `abstract` mot clé contextuel suivant de la classe, nom et avant le corps de la classe, une liste de dérivation de classe de base ou un point-virgule.  
  
```  
public ref class Shape abstract {};  
public ref class Shape2D abstract : public Shape{};  
```  
  
 Naturellement, la signification sémantique reste inchangée.  
  
## <a name="specifying-the-class-as-sealed"></a>Spécification de la classe comme Sealed  
 Sous les Extensions managées, vous placez le mot clé `__sealed` avant la `class` (mot clé) (soit avant soit après `__gc`) pour indiquer que les objets de la classe ne peut pas être héritées :  
  
```  
public __gc __sealed class String {};  
```  
  
 Dans la nouvelle syntaxe, vous spécifiez le `sealed` mot clé contextuel suivant de la classe, nom et avant le corps de la classe, une liste de dérivation de classe de base ou un point-virgule.  
  
 Vous pouvez dériver une classe et faites-le. Par exemple, le `String` classe est implicitement dérivée de `Object`. L’avantage de sceller une classe est prise en charge la résolution statique (autrement dit, au moment de la compilation) de tous les appels de fonction virtuelle via l’objet de classe de référence sealed. C’est parce que le `sealed` spécificateur garantit que le `String` handle de suivi ne peut pas faire référence à une classe dérivée ultérieurement qui peut fournir une instance de substitution de la méthode virtuelle appelée. Voici un exemple d’une classe sealed dans nouvelle syntaxe :  
  
```  
public ref class String sealed {};  
```  
  
 On peut également spécifier une classe comme abstract et sealed - il s’agit d’une condition spéciale qui indique une classe statique. Cela est décrit dans la documentation du CLR comme suit :  
  
 « Un type qui est à la fois `abstract` et `sealed` doivent avoir uniquement des membres statiques et sert de ce que certains langages appellent un espace de noms. »  
  
 Par exemple, voici une déclaration d’une classe abstraite sealed, à l’aide de la syntaxe des Extensions managées :  
  
```  
public __gc __sealed __abstract class State {  
public:  
   static State() {}  
   static bool inParamList();  
  
private:  
   static bool ms_inParam;  
};  
```  
  
 et voici cette déclaration traduite dans la nouvelle syntaxe :  
  
```  
public ref class State abstract sealed {  
public:  
   static State();  
   static bool inParamList();  
  
private:  
   static bool ms_inParam;  
};  
```  
  
## <a name="clr-inheritance-specifying-the-base-class"></a>Héritage CLR : Spécification de la classe de Base  
 Sous le modèle objet CLR, seul l’héritage public seul est pris en charge. Toutefois, les Extensions managées conservé l’interprétation par défaut ISO-C++ d’une classe de base sans mot clé d’accès spécifiant une dérivation privée. Cela signifiait que chaque déclaration de l’héritage CLR devait fournir le `public` mot clé pour substituer l’interprétation par défaut.  
  
```  
// Managed Extensions: error: defaults to private derivation  
__gc class Derived : Base {};  
```  
  
 Dans la nouvelle définition de la syntaxe, l’absence d’un mot clé d’accès indique une dérivation publique dans une définition d’héritage CLR. Par conséquent, le `public` mot clé d’accès est maintenant facultatif. Alors que cela ne nécessite pas de toute modification des Extensions managées pour le code C++, j’ai liste cette modification ici par souci d’exhaustivité.  
  
```  
// New syntax: ok: defaults to public derivation  
ref class Derived : Base{};  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Types managés (C + c++ / CL)](../dotnet/managed-types-cpp-cl.md)   
 [Classes et structs](../windows/classes-and-structs-cpp-component-extensions.md)   
 [abstract](../windows/abstract-cpp-component-extensions.md)   
 [sealed](../windows/sealed-cpp-component-extensions.md)