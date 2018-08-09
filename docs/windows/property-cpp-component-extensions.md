---
title: propriété (Extensions du composant C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- property_cpp
- property
dev_langs:
- C++
helpviewer_keywords:
- property keyword [C++]
ms.assetid: cc79d2b2-f013-4d81-8252-eece97a18704
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a1a90f0d72c824f3f4840728e34c01667e4aa026
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011602"
---
# <a name="property--c-component-extensions"></a>propriété  (extensions du composant C++)
Déclare un *propriété*, qui est une fonction membre qui se comporte et est accessible comme un membre de données ou un élément de tableau.  
  
## <a name="all-runtimes"></a>Tous les runtimes  
 Vous pouvez déclarer un des types de propriétés suivants.  
  
 *propriété simple*  
 Par défaut, crée un *accesseur set* qui assigne la valeur de propriété, un *accesseur get* qui Récupère la valeur de propriété et un membre généré par le compilateur les données privées qui contient la valeur de propriété.  
  
 *bloc de propriété*  
 Utilisez-le pour créer des accesseurs get et/ou set définis par l’utilisateur. La propriété est en lecture/écriture si les accesseurs get et set sont définis, en lecture seule si seul l'accesseur get est défini et en écriture seule si seul l'accesseur set est défini.  
  
 Vous devez déclarer explicitement un membre de données pour qu'il contienne la valeur de la propriété.  
  
 *propriété indexée*  
 Bloc de propriété que vous pouvez utiliser pour obtenir et définir une valeur de propriété qui est spécifiée par un ou plusieurs index.  
  
 Vous pouvez créer une propriété indexée qui a un nom de propriété défini par l’utilisateur ou un *par défaut* nom de la propriété. Le nom d'une propriété d'index par défaut correspond au nom de la classe dans laquelle la propriété est définie. Pour déclarer une propriété par défaut, spécifiez la **par défaut** mot-clé au lieu d’un nom de propriété.  
  
 Vous devez déclarer explicitement un membre de données pour qu'il contienne la valeur de la propriété. Pour une propriété indexée, le membre de données est en général un tableau ou une collection.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
property type property_name;

property type property_name { 
   access-modifier type get() inheritance-modifier {property_body}; 
   access-modifier void set(type value) inheritance-modifier {property_body};
} 

property type property_name[index_list] { 
   access-modifier type get(index_list) inheritance-modifier {property_body}; 
   access-modifier void set(index_list, value) inheritance-modifier {property_body};
} 

property type default[index_list] { 
   access-modifier type get(index_list) inheritance-modifier {property_body};
   access-modifier void set(index_list, value) inheritance-modifier {property_body};
}  
```  
  
### <a name="parameters"></a>Paramètres  
 *type*  
 Type de données de la valeur de la propriété et donc la propriété proprement dite.  
  
 *property_name*  
 Nom de la propriété.  
  
 *modificateur d’accès*  
 Qualificateur d'accès. Qualificateurs valides sont **statique** et **virtuel**.  
  
 La méthode get ou les accesseurs set n’accordent pas sur le **virtuel** qualificateur, mais ils doivent s’accorder sur le **statique** qualificateur.  
  
 *modificateur d’héritage*  
 Qualificateur d'héritage. Qualificateurs valides sont **abstraite** et **sealed**.  
  
 *index_list*  
 Liste délimitée par des virgules d'un ou plusieurs index. Chaque index se compose d'un type d'index et d'un identificateur facultatif qui peut être utilisé dans le corps de la méthode de propriété.  
  
 *valeur*  
 Valeur à affecter à la propriété dans une opération set ou à récupérer dans une opération get.  
  
 *property_body*  
 Corps de la méthode de propriété de l’accesseur set ou get. Le *property_body* pouvez utiliser la *index_list* pour accéder au membre de données de propriété sous-jacent, ou en tant que paramètres lors du traitement défini par l’utilisateur.  
  
## <a name="windows-runtime"></a>Windows Runtime  
 Pour plus d’informations, consultez [propriétés (C++ / c++ / CX)](http://msdn.microsoft.com/library/windows/apps/hh755807.aspx).  
  
### <a name="requirements"></a>Configuration requise  
 Option du compilateur : `/ZW`  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
### <a name="syntax"></a>Syntaxe  
  
```cpp  
modifier property type property_name;

modifier property type property_name {
   modifier void set(type);
   modifier type get();
}
modifier property type property_name[index-list, value] {
   modifier void set(index-list, value);
   modifier type get(index-list);

modifier property type default[index];
}  
```  
  
### <a name="parameters"></a>Paramètres  
  
 *Modificateur*  
 Modificateur qui peut être utilisé sur une déclaration de propriété ou une méthode d’accesseur get/set. Les valeurs possibles sont **statique** et **virtuel**.  
  
 *type*  
 Type de la valeur représentée par la propriété.  
  
 *property_name*  
 Paramètre(s) de la méthode raise ; doit correspondre à la signature du délégué.  
  
 *index_list*  
 Liste délimitée par des virgules d'un ou plusieurs index, spécifiés entre crochets (opérateur d'indice, ([])). Pour chaque index, spécifiez un type et éventuellement un identificateur qui peut être utilisé dans le corps de la méthode de propriété.  
  
### <a name="remarks"></a>Notes  
  
 Le premier exemple de syntaxe montre une *propriété simple*, qui déclare implicitement à la fois un `set` et `get` (méthode). Le compilateur crée automatiquement un champ privé pour stocker la valeur de la propriété.  
  
 Le deuxième exemple de syntaxe montre une *bloc property*, qui déclare explicitement un `set` et `get` (méthode).  
  
 Le troisième exemple de syntaxe montre une définie par le client *index, propriété*. Une propriété d'index prend des paramètres, en plus de la valeur à définir ou à récupérer. Vous devez spécifier un nom pour la propriété. Contrairement à une propriété simple, les méthodes `set` et/ou `get` d'une propriété d'index doivent être définies explicitement, et vous devez spécifier un nom pour la propriété.  
  
 Le quatrième exemple de syntaxe montre une *par défaut* propriété, qui fournit l’accès de type tableau à une instance du type. Le mot clé, **par défaut**, sert uniquement à spécifier une propriété par défaut. Le nom de la propriété par défaut correspond au nom du type dans lequel la propriété est définie.  
  
 Le **propriété** mot clé peut apparaître dans une classe, une interface ou un type valeur. Une propriété peut avoir une fonction get (lecture seule), une fonction set (écriture seule) ou les deux (lecture-écriture).  
  
 Un nom de propriété ne peut pas correspondre au nom de la classe managée qui la contient. Le type de retour de la fonction d’accesseur Get doit correspondre au type du dernier paramètre d’une fonction d’accesseur Set correspondante.  
  
 Pour le code client, une propriété a l'apparence d'un membre de données ordinaire et peut être écrite ou lu à l'aide de la même syntaxe qu'un membre de données.  
  
 La méthode get et les méthodes set n’accordent pas sur le **virtuel** modificateur.  
  
 L'accessibilité des méthodes get et set peut différer.  
  
 La définition d'une méthode de propriété peut apparaître en dehors du corps de la classe, comme une méthode ordinaire.  
  
 La méthode get et la méthode set pour une propriété doit s’accorder sur le **statique** modificateur.  
  
 Une propriété est scalaire si ses méthodes get et set correspondent à la description suivante :  
  
-   La méthode get n'a aucun paramètre et son type de retour est `T`.  
  
-   La méthode set possède un paramètre de type `T`et le type de retour **void**.  
  
 Il ne doit y avoir qu'une seule propriété scalaire déclarée dans une portée avec le même identificateur. Les propriétés scalaires ne peuvent pas être surchargées.  
  
 Quand un membre de données de propriété est déclaré, le compilateur injecte un membre de données (parfois appelé le « magasin de stockage ») dans la classe. Toutefois, le nom du membre de données est tel que vous ne pouvez pas référencer le membre dans la source comme s'il s'agissait d'un membre de données réel de la classe conteneur. Utilisez ildasm.exe pour afficher les métadonnées de votre type et voir le nom généré par le compilateur pour le magasin de stockage de la propriété.  
  
 Une accessibilité différente est autorisée pour les méthodes d'accesseur dans un bloc de propriété.  Autrement dit, la méthode set peut être publique et la méthode get peut être privée.  Toutefois, c’est une erreur pour une méthode d’accesseur d’avoir une accessibilité moins restrictive que celle figurant dans la déclaration de la propriété proprement dite.  
  
 **propriété** est un mot clé contextuel.  Pour plus d’informations, consultez [mots clés contextuels](../windows/context-sensitive-keywords-cpp-component-extensions.md).  
  
  
### <a name="requirements"></a>Configuration requise  
 Option du compilateur : `/clr`  
  
### <a name="examples"></a>Exemples  
 L'exemple suivant illustre la déclaration et l'utilisation d'un membre de données de propriété et d'un bloc de propriété.  Il montre également qu’un accesseur de propriété peut être défini en dehors d’une classe.  
  
```cpp  
// mcppv2_property.cpp  
// compile with: /clr  
using namespace System;  
public ref class C {  
   int MyInt;  
public:  
  
   // property data member  
   property String ^ Simple_Property;  
  
   // property block  
   property int Property_Block {  
  
      int get();  
  
      void set(int value) {  
         MyInt = value;  
      }  
   }  
};  
  
int C::Property_Block::get() {  
   return MyInt;  
}  
  
int main() {  
   C ^ MyC = gcnew C();  
   MyC->Simple_Property = "test";  
   Console::WriteLine(MyC->Simple_Property);  
  
   MyC->Property_Block = 21;  
   Console::WriteLine(MyC->Property_Block);  
}  
```  
  
```Output  
test  
  
21  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)