---
title: "property  (C++ Component Extensions) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "property_cpp"
  - "property"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "property keyword [C++]"
ms.assetid: cc79d2b2-f013-4d81-8252-eece97a18704
caps.latest.revision: 31
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# property  (C++ Component Extensions)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Déclare une *propriété*, qui est une fonction membre qui se comporte et est accessible comme un membre de données ou un élément de tableau.  
  
## Tous les runtimes  
 Vous pouvez déclarer un des types de propriétés suivants.  
  
 *propriété simple*  
 Par défaut, crée un *accesseur set* qui assigne la valeur de la propriété, un *accesseur get* qui récupère la valeur de la propriété et un membre de données privé généré par le compilateur qui contient la valeur de la propriété.  
  
 *bloc de propriété*  
 Utilisez\-le pour créer des accesseurs get et\/ou set définis par l'utilisateur.  La propriété est en lecture\/écriture si les accesseurs get et set sont définis, en lecture seule si seul l'accesseur get est défini et en écriture seule si seul l'accesseur set est défini.  
  
 Vous devez déclarer explicitement un membre de données pour qu'il contienne la valeur de la propriété.  
  
 *propriété indexée*  
 Bloc de propriété que vous pouvez utiliser pour obtenir et définir une valeur de propriété qui est spécifiée par un ou plusieurs index.  
  
 Vous pouvez créer une propriété indexée qui porte un nom de propriété défini par l'utilisateur ou un nom de propriété *par défaut*.  Le nom d'une propriété d'index par défaut correspond au nom de la classe dans laquelle la propriété est définie.  Pour déclarer une propriété par défaut, spécifiez le mot clé `default` au lieu d'un nom de propriété.  
  
 Vous devez déclarer explicitement un membre de données pour qu'il contienne la valeur de la propriété.  Pour une propriété indexée, le membre de données est en général un tableau ou une collection.  
  
### Syntaxe  
  
```cpp  
  
property type property_name;  
  
property type property_name {  
   access-modifier type get() inheritance-modifier {property_body};  
   access-modifier void set(type value) inheritance-modifier {property_body};  
} property type property_name[index_list] {  
   access-modifier type get(index_list) inheritance-modifier {property_body};  
   access-modifier void set(index_list, value) inheritance-modifier {property_body};  
} property type default[index_list] {  
   access-modifier type get(index_list) inheritance-modifier {property_body};  
   access-modifier void set(index_list, value) inheritance-modifier {property_body};  
}  
  
```  
  
### Paramètres  
 `type`  
 Type de données de la valeur de la propriété et donc la propriété proprement dite.  
  
 `property_name`  
 Nom de la propriété.  
  
 `access-modifier`  
 Qualificateur d'accès.  Les qualificateurs valides sont `static` et `virtual`.  
  
 Les accesseurs get ou set n'ont pas besoin de s'accorder sur le qualificateur `virtual`, mais ils doivent s'accorder sur le qualificateur `static`.  
  
 `inheritance-modifier`  
 Qualificateur d'héritage.  Les qualificateurs valides sont `abstract` et `sealed`.  
  
 `index_list`  
 Liste délimitée par des virgules d'un ou plusieurs index.  Chaque index se compose d'un type d'index et d'un identificateur facultatif qui peut être utilisé dans le corps de la méthode de propriété.  
  
 `value`  
 Valeur à affecter à la propriété dans une opération set ou à récupérer dans une opération get.  
  
 `property_body`  
 Corps de la méthode de propriété de l'accesseur set ou get.  Le `property_body` peut utiliser la `index_list` pour accéder au membre de données de propriété sous\-jacent, ou en tant que paramètres dans le cadre du traitement défini par l'utilisateur.  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 Pour plus d'informations, consultez [Propriétés \(C\+\+\/CX\)](http://msdn.microsoft.com/library/windows/apps/hh755807.aspx).  
  
### Spécifications  
 Option du compilateur : **\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **Syntaxe**  
  
```  
  
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
  
 **Paramètres**  
  
 *modificateur*  
 Modificateur qui peut être utilisé sur une déclaration de propriété ou une méthode d'accesseur get\/set.  Les valeurs possibles sont `static` et `virtual`.  
  
 *type*  
 Type de la valeur représentée par la propriété.  
  
 *nom\_propriété*  
 Paramètre\(s\) de la méthode raise ; doit correspondre à la signature du délégué.  
  
 *liste\_index*  
 Liste délimitée par des virgules d'un ou plusieurs index, spécifiés entre crochets \(opérateur d'indice, \(\[\]\)\).  Pour chaque index, spécifiez un type et éventuellement un identificateur qui peut être utilisé dans le corps de la méthode de propriété.  
  
 **Notes**  
  
 Le premier exemple de syntaxe montre une *propriété simple*, qui déclare implicitement à la fois une méthode `set` et une méthode `get`.  Le compilateur crée automatiquement un champ privé pour stocker la valeur de la propriété.  
  
 Le deuxième exemple de syntaxe présente un *bloc de propriété*, qui déclare explicitement une méthode `set` et une méthode `get`.  
  
 Le troisième exemple de syntaxe montre une *propriété d'index* définie par le client.  Une propriété d'index prend des paramètres, en plus de la valeur à définir ou à récupérer.  Vous devez spécifier un nom pour la propriété.  Contrairement à une propriété simple, les méthodes `set` et\/ou `get` d'une propriété d'index doivent être définies explicitement, et vous devez spécifier un nom pour la propriété.  
  
 Le quatrième exemple de syntaxe montre une propriété *par défaut*, qui fournit un accès de type tableau à une instance du type.  Le mot clé, `default`, sert uniquement à spécifier une propriété par défaut.  Le nom de la propriété par défaut correspond au nom du type dans lequel la propriété est définie.  
  
 Le mot clé `property` peut apparaître dans une classe, une interface ou un type valeur.  Une propriété peut avoir une fonction get \(lecture seule\), une fonction set \(écriture seule\) ou les deux \(lecture\-écriture\).  
  
 Un nom de propriété ne peut pas correspondre au nom de la classe managée qui la contient.  Le type de retour de la fonction d'accesseur Get doit correspondre au type du dernier paramètre d'une fonction d'accesseur Set correspondante.  
  
 Pour le code client, une propriété a l'apparence d'un membre de données ordinaire et peut être écrite ou lu à l'aide de la même syntaxe qu'un membre de données.  
  
 Les méthodes get et set ne s'accordent pas sur le modificateur `virtual`.  
  
 L'accessibilité des méthodes get et set peut différer.  
  
 La définition d'une méthode de propriété peut apparaître en dehors du corps de la classe, comme une méthode ordinaire.  
  
 La méthode get et set d'une propriété doit s'accorder sur le modificateur **static**.  
  
 Une propriété est scalaire si ses méthodes get et set correspondent à la description suivante :  
  
-   La méthode get n'a aucun paramètre et son type de retour est `T`.  
  
-   La méthode set possède un paramètre de type `T` et son type de retour est **void**.  
  
 Il ne doit y avoir qu'une seule propriété scalaire déclarée dans une portée avec le même identificateur.  Les propriétés scalaires ne peuvent pas être surchargées.  
  
 Quand un membre de données de propriété est déclaré, le compilateur injecte un membre de données \(parfois appelé le « magasin de stockage »\) dans la classe.  Toutefois, le nom du membre de données est tel que vous ne pouvez pas référencer le membre dans la source comme s'il s'agissait d'un membre de données réel de la classe conteneur.  Utilisez ildasm.exe pour afficher les métadonnées de votre type et voir le nom généré par le compilateur pour le magasin de stockage de la propriété.  
  
 Une accessibilité différente est autorisée pour les méthodes d'accesseur dans un bloc de propriété.  Autrement dit, la méthode set peut être publique et la méthode get peut être privée.  Toutefois, c'est une erreur pour une méthode d'accesseur d'avoir une accessibilité moins restrictive que celle figurant dans la déclaration de la propriété proprement dite.  
  
 `property` est un mot clé contextuel.  Pour plus d'informations, voir [Mots clés contextuels](../windows/context-sensitive-keywords-cpp-component-extensions.md).  
  
 Pour plus d'informations sur les propriétés, consultez  
  
-   [Propriétés indexées](../misc/how-to-use-indexed-properties.md)  
  
-   [Propriétés statiques](../misc/how-to-declare-and-use-static-properties.md)  
  
-   [Propriétés virtuelles](../misc/how-to-declare-and-use-virtual-properties.md)  
  
-   [Propriétés multidimensionnelles](../misc/how-to-use-multidimensional-properties.md)  
  
-   [Surcharge de méthodes d'accesseur de propriété](../misc/how-to-overload-property-accessor-methods.md)  
  
-   [Comment : déclarer un abstract et des propriétés sealed](../misc/how-to-declare-abstract-and-sealed-properties.md)  
  
### Spécifications  
 Option du compilateur : **\/clr**  
  
### Exemples  
 L'exemple suivant illustre la déclaration et l'utilisation d'un membre de données de propriété et d'un bloc de propriété.  Il montre également qu'un accesseur de propriété peut être défini en dehors d'une classe.  
  
```  
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
  
 **Sortie**  
  
  **test**  
 **21**   
## Voir aussi  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)