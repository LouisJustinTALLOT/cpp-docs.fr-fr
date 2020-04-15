---
title: Platform::Collections::Vector, classe
ms.date: 12/04/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::Vector::Vector
- COLLECTION/Platform::Collections::Vector::Append
- COLLECTION/Platform::Collections::Vector::Clear
- COLLECTION/Platform::Collections::Vector::First
- COLLECTION/Platform::Collections::Vector::GetAt
- COLLECTION/Platform::Collections::Vector::GetMany
- COLLECTION/Platform::Collections::Vector::GetView
- COLLECTION/Platform::Collections::Vector::IndexOf
- COLLECTION/Platform::Collections::Vector::InsertAt
- COLLECTION/Platform::Collections::Vector::ReplaceAll
- COLLECTION/Platform::Collections::Vector::RemoveAt
- COLLECTION/Platform::Collections::Vector::RemoveAtEnd
- COLLECTION/Platform::Collections::Vector::SetAt
- COLLECTION/Platform::Collections::Vector::Size
- COLLECTION/Platform::Collections::Vector::VectorChanged
helpviewer_keywords:
- Vector Class (C++/Cx)
ms.assetid: aee8c076-9700-47c3-99b6-799fd3edb0ca
ms.openlocfilehash: b2d08461b4ab57ed8479549c18c35c872d0eb9f1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354386"
---
# <a name="platformcollectionsvector-class"></a>Platform::Collections::Vector, classe

Représente une collection séquentielle d'objets accessibles séparément par index. Implémente [Windows::Foundation:Collections::IObservableVector](/uwp/api/Windows.Foundation.Collections.IObservableVector_T_) pour aider avec XAML [liaison de données](/windows/uwp/data-binding/data-binding-in-depth).

## <a name="syntax"></a>Syntaxe

```
template <typename T, typename E>
   ref class Vector sealed;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type des éléments contenus dans l'objet Vector.

*E*<br/>
Spécifie un prédicat binaire pour tester l’égalité avec des valeurs de type *T*. La valeur `std::equal_to<T>`par défaut est .

### <a name="remarks"></a>Notes

Les types autorisés sont :

1. Entiers

1. classe d’interface

1. Classe ref publique ^

1. value struct

1. classe d'énumération publique

La classe **Vector** est la mise en œuvre concrète de [Windows::Foundation::Collections::IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_) interface.

Si vous essayez d’utiliser un type **Vector** dans une valeur ou un paramètre de retour public, l’erreur de compilateur C3986 est soulevée. Vous pouvez corriger l'erreur en modifiant le type du paramètre ou le type de la valeur de retour par [Windows::Foundation::Collections::IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_). Pour plus d'informations, consultez [Collections (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Vecteur::Vector](#ctor)|Initialise une nouvelle instance de la classe Vector.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Vector::Append](#append)|Insère l'élément spécifié après le dernier élément du Vector actif.|
|[Vecteur::Clair](#clear)|Supprime tous les éléments du vecteur actuel.|
|[Vecteur::Première](#first)|Retourne un itérateur qui spécifie le premier élément du Vector.|
|[Vecteur::GetAt](#getat)|Récupère l'élément de l'objet Vector actuel qui est identifié par l'index spécifié.|
|[Vecteur::GetMany](#getmany)|Récupère une séquence d'éléments du Vector actif en commençant à l'index spécifié.|
|[Vecteur::GetView](#getview)|Retourne une vue en lecture seule d'un vecteur ; autrement dit, une [Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md).|
|[Vecteur::IndexOf](#indexof)|Recherche l'élément spécifié dans l'objet Vector actuel, et s'il existe, retourne l'index de l'élément.|
|[Vector::InsertAt](#insertat)|Insère l’élément spécifié dans le vecteur actuel à l’élément identifié par l’index spécifié.|
|[Vector::ReplaceAll](#replaceall)|Supprime les éléments du Vector actif et les insère depuis le tableau spécifié.|
|[Vector::RemoveAt](#removeat)|Supprime l'élément identifié par l'index spécifié à partir du Vector actif.|
|[Vector::RemoveAtEnd](#removeatend)|Supprime l'élément à la fin du Vector actif.|
|[Vector::SetAt](#setat)|Assigne la valeur spécifiée à l'élément du Vector actif identifié par l'index spécifié.|
|[Vecteur::Taille](#size)|Retourne le nombre d'éléments dans l'objet Vector actuel.|

### <a name="events"></a>Événements

|||
|-|-|
|Nom|Description|
|événement [Windows::Fondation::Collection::VectorChangedEventHandler\<T>-VectorChanged](/uwp/api/windows.foundation.collections.vectorchangedeventhandler)|Se produit lorsque le Vector est modifié.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Vector`

### <a name="requirements"></a>Spécifications

**En-tête :** collection.h

**Espace de noms :** Platform::Collections

## <a name="vectorappend-method"></a><a name="append"></a>Vecteur::Méthode d’append

Insère l'élément spécifié après le dernier élément du Vector actif.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Append(T item);
```

### <a name="parameters"></a>Paramètres

*index*<br/>
Élément à insérer dans le Vector. Le type *d’article* est défini par le nom de type *T.*

## <a name="vectorclear-method"></a><a name="clear"></a>Vecteur::Méthode claire

Supprime tous les éléments du vecteur actuel.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Clear();
```

## <a name="vectorfirst-method"></a><a name="first"></a>Vecteur::Première méthode

Retourne un itérateur qui pointe vers le premier élément du Vector.

### <a name="syntax"></a>Syntaxe

```cpp
virtual Windows::Foundation::Collections::IIterator <T>^ First();
```

### <a name="return-value"></a>Valeur de retour

Itérateur qui pointe vers le premier élément du Vector.

### <a name="remarks"></a>Notes

Une façon pratique de tenir l’itérateur retourné par First() est d’attribuer la valeur de retour à une variable qui est déclarée avec le mot clé de déduction de type **automatique.** Par exemple : `auto x = myVector->First();`. Cet itérateur connaît la longueur de la collection.

Lorsque vous avez besoin d’une paire d’itérateurs pour passer à une fonction STL, utilisez les fonctions gratuites [Windows::Foundation::Collections::commencer](../cppcx/begin-function.md) et [Windows::Foundation:Collections::fin](../cppcx/end-function.md)

## <a name="vectorgetat-method"></a><a name="getat"></a>Vecteur::GetAt Méthode

Récupère l'élément de l'objet Vector actuel qui est identifié par l'index spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
virtual T GetAt(unsigned int index);
```

### <a name="parameters"></a>Paramètres

*index*<br/>
Entier non signé de base zéro qui spécifie un élément particulier dans l'objet Vector.

### <a name="return-value"></a>Valeur de retour

L’élément spécifié par le paramètre *de l’index.* Le type d’élément est défini par le nom de type *T.*

## <a name="vectorgetmany-method"></a><a name="getmany"></a>Vecteur::GetMany Méthode

Récupère une séquence d'éléments du Vector actif en commençant à l'index spécifié et les copie dans le tableau alloué par l'appelant.

### <a name="syntax"></a>Syntaxe

```cpp
virtual unsigned int GetMany(
    unsigned int startIndex,
    Platform::WriteOnlyArray<T>^ dest);
```

### <a name="parameters"></a>Paramètres

*Startindex*<br/>
L'index de base zéro du début des éléments à récupérer.

*dest*<br/>
Un tableau d’éléments attribué à l’appelant qui commence à l’élément spécifié par *startIndex* et se terminent au dernier élément du Vector.

### <a name="return-value"></a>Valeur de retour

Le nombre d'éléments à récupérer.

### <a name="remarks"></a>Notes

Cette fonction n'est pas destinée à être utilisée directement par le code client. Il est utilisé en interne dans la [fonction to_vector](../cppcx/to-vector-function.md) pour permettre une conversion efficace de la plate-forme::Vector intances à std::vector instances.

## <a name="vectorgetview-method"></a><a name="getview"></a>Vecteur::GetView Méthode

Retourne une vue en lecture seule d'un Vector, c'est-à-dire un IVectorView.

### <a name="syntax"></a>Syntaxe

```cpp
Windows::Foundation::Collections::IVectorView<T>^ GetView();
```

### <a name="return-value"></a>Valeur de retour

Objet IVectorView.

## <a name="vectorindexof-method"></a><a name="indexof"></a>Vecteur::IndexOf Méthode

Recherche l'élément spécifié dans l'objet Vector actuel, et s'il existe, retourne l'index de l'élément.

### <a name="syntax"></a>Syntaxe

```cpp
virtual bool IndexOf(T value, unsigned int* index);
```

### <a name="parameters"></a>Paramètres

*value*<br/>
Élément à rechercher.

*index*<br/>
L’indice à base nulle de l’élément si *l’on* trouve la valeur du paramètre; autrement, 0.

Le paramètre *de l’index* est de 0 si l’élément est le premier élément du vecteur ou si l’élément n’a pas été trouvé. Si la valeur de rendement est **vraie,** l’article a été trouvé et c’est le premier élément; autrement, l’article n’a pas été trouvé.

### <a name="return-value"></a>Valeur de retour

**vrai** si l’élément spécifié est trouvé; autrement, **faux**.

### <a name="remarks"></a>Notes

IndexOf uses std::find_if pour trouver l'élément. Les types d'élément personnalisés doivent surcharger les opérateurs == et != afin d'autoriser les comparaisons d'égalité requises par find_if.

## <a name="vectorinsertat-method"></a><a name="insertat"></a>Vecteur::InsertAt Méthode

Insère l’élément spécifié dans le vecteur actuel à l’élément identifié par l’index spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void InsertAt(unsigned int index, T item)
```

### <a name="parameters"></a>Paramètres

*index*<br/>
Entier non signé de base zéro qui spécifie un élément particulier dans l'objet Vector.

*item*<br/>
Un élément à insérer dans le vecteur à l’élément spécifié par *index*. Le type *d’article* est défini par le nom de type *T.*

## <a name="vectorremoveat-method"></a><a name="removeat"></a>Vecteur::RemoveAt Méthode

Supprime l'élément identifié par l'index spécifié à partir du Vector actif.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void RemoveAt(unsigned int index);
```

### <a name="parameters"></a>Paramètres

*index*<br/>
Entier non signé de base zéro qui spécifie un élément particulier dans l'objet Vector.

## <a name="vectorremoveatend-method"></a><a name="removeatend"></a>Vecteur::RemoveAtEnd Méthode

Supprime l'élément à la fin du Vector actif.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void RemoveAtEnd();
```

## <a name="vectorreplaceall-method"></a><a name="replaceall"></a>Vecteur::ReplaceAll Méthode

Supprime les éléments du Vector actif et les insère depuis le tableau spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void ReplaceAll(const ::Platform::Array<T>^ arr);
```

### <a name="parameters"></a>Paramètres

*Arr*<br/>
Une gamme d’objets dont le type est défini par le nom de type *T.*

## <a name="vectorsetat-method"></a><a name="setat"></a>Vecteur::SetAt Méthode

Assigne la valeur spécifiée à l'élément du Vector actif identifié par l'index spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void SetAt(unsigned int index, T item);
```

### <a name="parameters"></a>Paramètres

*index*<br/>
Entier non signé de base zéro qui spécifie un élément particulier dans l'objet Vector.

*item*<br/>
Valeur à assigner à l’élément spécifié. Le type *d’article* est défini par le nom de type *T.*

## <a name="vectorsize-method"></a><a name="size"></a>Vecteur::Méthode de taille

Retourne le nombre d'éléments dans l'objet Vector actuel.

### <a name="syntax"></a>Syntaxe

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments dans l’objet Vector actuel.

## <a name="vectorvector-constructor"></a><a name="ctor"></a>Vecteur::Vector Constructor

Initialise une nouvelle instance de la classe Vector.

### <a name="syntax"></a>Syntaxe

```cpp
Vector();

explicit Vector(unsigned int size);
Vector( unsigned int size, T value);
template <typename U> explicit Vector( const ::std::vector<U>& v);
template <typename U> explicit Vector( std::vector<U>&& v);

Vector( const T * ptr, unsigned int size);
template <size_t N> explicit Vector(const T(&arr)[N]);
template <size_t N> explicit Vector(const std::array<T, N>& a);
explicit Vector(const Array<T>^ arr);

template <typename InIt> Vector(InIt first, InIt last);
Vector(std::initializer_list<T> il);
```

### <a name="parameters"></a>Paramètres

*Un*<br/>
Un [std::array](../standard-library/array-class-stl.md) qui sera utilisé pour initialiser le vecteur.

*Arr*<br/>
Une [plate-forme::Array](../cppcx/platform-array-class.md) qui sera utilisé pour initialiser le vecteur.

*Init*<br/>
Type d’une collection d’objets utilisée pour initialiser l’objet Vector actuel.

*il*<br/>
Un [std::initializer_list](../standard-library/initializer-list-class.md) d’objets de type *T* qui seront utilisés pour initialiser le vecteur.

*Â¡n*<br/>
Nombre d’éléments d’une collection d’objets utilisée pour initialiser l’objet Vector actuel.

*Taille*<br/>
Nombre d'éléments dans l'objet Vector.

*value*<br/>
Valeur utilisée pour initialiser chaque élément de l'objet Vector actuel.

*C*<br/>
Un [Lvalues et Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) à un [std::vector](../standard-library/vector-class.md) qui est utilisé pour initialiser le vecteur actuel.

*Ptr*<br/>
Pointeur vers un `std::vector` utilisé pour initialiser l'objet Vector actuel.

*Première*<br/>
Premier élément d'une séquence d'objets utilisée pour initialiser l'objet Vector actuel. Le type de *premier* est passé au moyen de *l’avance parfaite*. Pour plus d'informations, consultez [Déclarateur de référence rvalue : &&](../cpp/rvalue-reference-declarator-amp-amp.md).

*Dernière*<br/>
Dernier élément d'une séquence d'objets utilisée pour initialiser l'objet Vector actuel. Le type de *dernier* est passé au moyen de *l’avance parfaite*. Pour plus d'informations, consultez [Déclarateur de référence rvalue : &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Voir aussi

[Collections (C/CX)](collections-c-cx.md)<br/>
[Espace nom de la plate-forme](platform-namespace-c-cx.md)<br/>
[Création de composants Windows Runtime en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
