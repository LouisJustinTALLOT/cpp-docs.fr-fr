---
title: Platform::Object, classe | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Object::Object
- VCCORLIB/Platform::Object::Equals
- VCCORLIB/Platform::Object::GetHashCode
- VCCORLIB/Platform::Object::ReferenceEquals
- VCCORLIB/Platform::ToString
- VCCORLIB/Platform::GetType
dev_langs:
- C++
helpviewer_keywords:
- Object class
ms.assetid: 709e84a8-0bff-471b-bc14-63e424080b5a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 19c302f08485b6db89ea2a6b66106244ed95b48c
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601736"
---
# <a name="platformobject-class"></a>Platform::Object, classe
Fournit un comportement commun pour les classes ou structs ref dans les applications Windows Runtime. Toute instance de classe ref ou de struct ref est implicitement convertible en objet Platform::Object^ et peut remplacer sa méthode ToString virtuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
public ref class Object : Object  
```  
  
### <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[Object::Object](#ctor)|Initialise une nouvelle instance de la classe Object.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[Object::Equals](#equals)|Détermine si l'objet spécifié est identique à l'objet actuel.|  
|[Object::GetHashCode](#gethashcode)|Retourne le code de hachage de cette instance.|  
|[Object::ReferenceEquals](#referenceequals)|Détermine si les instances Object spécifiées sont identiques.|  
|[ToString](#tostring)|Retourne une chaîne qui représente l'objet actuel. Peut être substituée.|  
|[GetType](#gettype)|Obtient un [Platform::Type](../cppcx/platform-type-class.md) qui décrit l'instance actuelle.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `Object`  
  
 `Object`  
  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** vccorlib.h  
  
 **Espace de noms :** Platform  

  
## <a name="equals"></a> Object::Equals, méthode
Détermine si l'objet spécifié est identique à l'objet actuel.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
bool Equals(  
    Object^ obj  
)  
```  
  
### <a name="parameters"></a>Paramètres  
 obj  
 Objet à comparer.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` si les objets sont identiques ; sinon, `false`.  
  


## <a name="gethashcode"></a>  Object::GetHashCode, méthode
Retourne la valeur d'identité `IUnknown`* pour cette instance s'il s'agit d'un objet COM ou une valeur de hachage calculée s'il ne s'agit d'un objet COM.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:int GetHashCode()  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur numérique qui identifie de façon unique cet objet.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez utiliser GetHashCode afin de créer des clés pour les objets des cartes. Vous pouvez comparer les codes de hachage à l’aide de [Object::Equals](#equals). Si le chemin de code est extrêmement critique et `GetHashCode` et `Equals` ne sont pas suffisamment rapides, vous pouvez alors accéder à la couche COM sous-jacente et effectuer des comparaisons de pointeurs `IUnknown` natifs.  
  


## <a name="gettype"></a>  Object::GetType, méthode
Retourne un [Platform::Type](../cppcx/platform-type-class.md) objet qui décrit le type d’exécution d’un objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
Object::GetType()  
```  

  
### <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Un [Platform::Type](../cppcx/platform-type-class.md) objet qui décrit le type de runtime de l’objet.  
  
### <a name="remarks"></a>Notes  
 La méthode statique [Type::GetTypeCode](../cppcx/platform-type-class.md#gettypecode) peut être utilisé pour obtenir un [Platform::TypeCode Enumeration](../cppcx/platform-typecode-enumeration.md) valeur qui représente le type actuel. Ceci est particulièrement utile pour les types intégrés. Le code de type pour toute classe ref en plus [Platform::String](../cppcx/platform-string-class.md) est Object (1).  
  
 Le [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) classe est utilisée dans les API Windows comme un moyen indépendant du langage de passer des informations de type entre les composants de Windows et les applications. Le T[classe Platform::Type](../cppcx/platform-type-class.md) a des opérateurs de conversion entre `Type` et `TypeName`.  
  
 Utilisez le [typeid](../windows/typeid-cpp-component-extensions.md) opérateur pour retourner un `Platform::Type` objet pour un nom de classe, par exemple lors de la navigation entre les pages XAML :  
  
```  
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Classe Platform::type](../cppcx/platform-type-class.md)   
 [Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)   
 (Type System) (.. /cppcx/type-System-c-CX.MD
  
## <a name="ctor"></a>  Object::Object, constructeur
Initialise une nouvelle instance de la classe Object.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:Object()  
```  

## <a name="referenceequals"></a>  Object::ReferenceEquals, méthode
Détermine si les instances Object spécifiées sont identiques.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:static bool ReferenceEquals(  Object^ obj1,   Object^ obj2)  
```  
  
### <a name="parameters"></a>Paramètres  
 obj1  
 Premier objet à comparer.  
  
 obj2  
 Deuxième objet à comparer.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` si les deux objets sont identiques ; sinon, `false`.  
 
## <a name="tostring"></a>  Object::ToString, méthode (C++ / c++ / CX)
Retourne une chaîne qui représente l'objet actuel.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:  
virtual String^ ToString()  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Chaîne qui représente l'objet actuel. Vous pouvez substituer cette méthode afin de fournir un message personnalisé dans votre classe ou struct ref :  
  
```cpp  
public ref class Tree sealed  
{  
public:  
    Tree(){}  
    virtual Platform::String^ ToString() override  
    {  
      return "I’m a Tree";  
    };  
};  
```  
## <a name="see-also"></a>Voir aussi  
 [Plateforme Namespace](platform-namespace-c-cx.md)