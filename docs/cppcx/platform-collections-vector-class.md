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
ms.openlocfilehash: dc467b8db3cd6ec88395554eef7f109877f10d41
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839086"
---
# <a name="platformcollectionsvector-class"></a>Platform::Collections::Vector, classe

Représente une collection séquentielle d'objets accessibles séparément par index. Implémente [Windows :: Foundation :: Collections :: IObservableVector](/uwp/api/windows.foundation.collections.iobservablevector-1) pour faciliter la [liaison de données](/windows/uwp/data-binding/data-binding-in-depth)XAML.

## <a name="syntax"></a>Syntaxe

```
template <typename T, typename E>
   ref class Vector sealed;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type des éléments contenus dans l'objet Vector.

*Envoyer*<br/>
Spécifie un prédicat binaire pour tester l’égalité avec des valeurs de type *T*. La valeur par défaut est `std::equal_to<T>` .

### <a name="remarks"></a>Notes

Les types autorisés sont :

1. entiers

1. classe d’interface ^

1. Classe ref publique ^

1. value struct

1. classe d'énumération publique

La classe **Vector** est l’implémentation concrète C++ de l’interface [Windows :: Foundation :: Collections :: IVector](/uwp/api/windows.foundation.collections.ivector-1) .

Si vous tentez d’utiliser un type **Vector** dans une valeur ou un paramètre de retour public, l’erreur de compilateur C3986 est générée. Vous pouvez corriger l'erreur en modifiant le type du paramètre ou le type de la valeur de retour par [Windows::Foundation::Collections::IVector](/uwp/api/windows.foundation.collections.ivector-1). Pour plus d'informations, consultez [Collections (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Vector :: Vector](#ctor)|Initialise une nouvelle instance de la classe Vector.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Vector::Append](#append)|Insère l'élément spécifié après le dernier élément du Vector actif.|
|[Vector :: Clear](#clear)|Supprime tous les éléments du vecteur actuel.|
|[Vector :: First](#first)|Retourne un itérateur qui spécifie le premier élément du Vector.|
|[Vector :: GetAt](#getat)|Récupère l'élément de l'objet Vector actuel qui est identifié par l'index spécifié.|
|[Vector :: Getmany (](#getmany)|Récupère une séquence d'éléments du Vector actif en commençant à l'index spécifié.|
|[Vector :: GetView](#getview)|Retourne une vue en lecture seule d'un vecteur ; autrement dit, une [Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md).|
|[Vector :: IndexOf](#indexof)|Recherche l'élément spécifié dans l'objet Vector actuel, et s'il existe, retourne l'index de l'élément.|
|[Vector::InsertAt](#insertat)|Insère l’élément spécifié dans le vecteur actuel au niveau de l’élément identifié par l’index spécifié.|
|[Vector::ReplaceAll](#replaceall)|Supprime les éléments du Vector actif et les insère depuis le tableau spécifié.|
|[Vector::RemoveAt](#removeat)|Supprime l'élément identifié par l'index spécifié à partir du Vector actif.|
|[Vector::RemoveAtEnd](#removeatend)|Supprime l'élément à la fin du Vector actif.|
|[Vector::SetAt](#setat)|Assigne la valeur spécifiée à l'élément du Vector actif identifié par l'index spécifié.|
|[Vector :: Size](#size)|Retourne le nombre d'éléments dans l'objet Vector actuel.|

### <a name="events"></a>Événements

| Nom | Description |
|--|--|
| Event [Windows :: Foundation :: collection :: VectorChangedEventHandler \<T> ^ VectorChanged](/uwp/api/windows.foundation.collections.vectorchangedeventhandler-1) | Se produit lorsque le Vector est modifié. |

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Vector`

### <a name="requirements"></a>Configuration requise

**En-tête :** collection.h

**Espace de noms :** Platform::Collections

## <a name="vectorappend-method"></a><a name="append"></a> Vector :: Append, méthode

Insère l'élément spécifié après le dernier élément du Vector actif.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Append(T item);
```

### <a name="parameters"></a>Paramètres

*index*<br/>
Élément à insérer dans le Vector. Le type d' *élément* est défini par le TypeName *T* .

## <a name="vectorclear-method"></a><a name="clear"></a> Vector :: Clear, méthode

Supprime tous les éléments du vecteur actuel.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Clear();
```

## <a name="vectorfirst-method"></a><a name="first"></a> Vector :: First, méthode

Retourne un itérateur qui pointe vers le premier élément du Vector.

### <a name="syntax"></a>Syntaxe

```cpp
virtual Windows::Foundation::Collections::IIterator <T>^ First();
```

### <a name="return-value"></a>Valeur de retour

Itérateur qui pointe vers le premier élément du Vector.

### <a name="remarks"></a>Notes

Un moyen pratique de contenir l’itérateur retourné par First () consiste à affecter la valeur de retour à une variable déclarée avec le **`auto`** mot clé de déduction de type. Par exemple : `auto x = myVector->First();`. Cet itérateur connaît la longueur de la collection.

Quand vous avez besoin d’une paire d’itérateurs à passer à une fonction STL, utilisez les fonctions gratuites [Windows :: Foundation :: Collections :: Begin](../cppcx/begin-function.md) et [Windows :: Foundation :: Collections :: end](../cppcx/end-function.md)

## <a name="vectorgetat-method"></a><a name="getat"></a> Vector :: GetAt, méthode

Récupère l'élément de l'objet Vector actuel qui est identifié par l'index spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
virtual T GetAt(unsigned int index);
```

### <a name="parameters"></a>Paramètres

*index*<br/>
Entier non signé de base zéro qui spécifie un élément particulier dans l'objet Vector.

### <a name="return-value"></a>Valeur renvoyée

Élément spécifié par le paramètre d' *index* . Le type d’élément est défini par le TypeName *T* .

## <a name="vectorgetmany-method"></a><a name="getmany"></a> Vector :: Getmany (, méthode

Récupère une séquence d'éléments du Vector actif en commençant à l'index spécifié et les copie dans le tableau alloué par l'appelant.

### <a name="syntax"></a>Syntaxe

```cpp
virtual unsigned int GetMany(
    unsigned int startIndex,
    Platform::WriteOnlyArray<T>^ dest);
```

### <a name="parameters"></a>Paramètres

*startIndex*<br/>
L'index de base zéro du début des éléments à récupérer.

*dest*<br/>
Tableau alloué par l’appelant des éléments qui commencent à l’élément spécifié par *startIndex* et se terminent au dernier élément du vecteur.

### <a name="return-value"></a>Valeur renvoyée

Le nombre d'éléments à récupérer.

### <a name="remarks"></a>Notes

Cette fonction n'est pas destinée à être utilisée directement par le code client. Elle est utilisée en interne dans la [fonction to_vector](../cppcx/to-vector-function.md) pour permettre une conversion efficace de Platform :: Vector instances en instances std :: Vector.

## <a name="vectorgetview-method"></a><a name="getview"></a> Vector :: GetView, méthode

Retourne une vue en lecture seule d'un Vector, c'est-à-dire un IVectorView.

### <a name="syntax"></a>Syntaxe

```cpp
Windows::Foundation::Collections::IVectorView<T>^ GetView();
```

### <a name="return-value"></a>Valeur de retour

Objet IVectorView.

## <a name="vectorindexof-method"></a><a name="indexof"></a> Vector :: IndexOf, méthode

Recherche l'élément spécifié dans l'objet Vector actuel, et s'il existe, retourne l'index de l'élément.

### <a name="syntax"></a>Syntaxe

```cpp
virtual bool IndexOf(T value, unsigned int* index);
```

### <a name="parameters"></a>Paramètres

*value*<br/>
Élément à rechercher.

*index*<br/>
Index de base zéro de l’élément si la *valeur* du paramètre est trouvée ; Sinon, 0.

Le paramètre d' *index* est 0 si l’élément est le premier élément du vecteur ou si l’élément est introuvable. Si la valeur de retour est **`true`** , l’élément a été trouvé et il s’agit du premier élément ; sinon, l’élément est introuvable.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l’élément spécifié est trouvé ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

IndexOf uses std::find_if pour trouver l'élément. Les types d'élément personnalisés doivent surcharger les opérateurs == et != afin d'autoriser les comparaisons d'égalité requises par find_if.

## <a name="vectorinsertat-method"></a><a name="insertat"></a> Vector :: InsertAt, méthode

Insère l’élément spécifié dans le vecteur actuel au niveau de l’élément identifié par l’index spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void InsertAt(unsigned int index, T item)
```

### <a name="parameters"></a>Paramètres

*index*<br/>
Entier non signé de base zéro qui spécifie un élément particulier dans l'objet Vector.

*item*<br/>
Élément à insérer dans le vecteur au niveau de l’élément spécifié par l' *index*. Le type d' *élément* est défini par le TypeName *T* .

## <a name="vectorremoveat-method"></a><a name="removeat"></a> Vector :: RemoveAt, méthode

Supprime l'élément identifié par l'index spécifié à partir du Vector actif.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void RemoveAt(unsigned int index);
```

### <a name="parameters"></a>Paramètres

*index*<br/>
Entier non signé de base zéro qui spécifie un élément particulier dans l'objet Vector.

## <a name="vectorremoveatend-method"></a><a name="removeatend"></a> Vector :: Removeatend,, méthode

Supprime l'élément à la fin du Vector actif.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void RemoveAtEnd();
```

## <a name="vectorreplaceall-method"></a><a name="replaceall"></a> Vector :: ReplaceAll, méthode

Supprime les éléments du Vector actif et les insère depuis le tableau spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void ReplaceAll(const ::Platform::Array<T>^ arr);
```

### <a name="parameters"></a>Paramètres

*arr*<br/>
Tableau d’objets dont le type est défini par le TypeName *T* .

## <a name="vectorsetat-method"></a><a name="setat"></a> Vector :: SetAt, méthode

Assigne la valeur spécifiée à l'élément du Vector actif identifié par l'index spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void SetAt(unsigned int index, T item);
```

### <a name="parameters"></a>Paramètres

*index*<br/>
Entier non signé de base zéro qui spécifie un élément particulier dans l'objet Vector.

*item*<br/>
Valeur à assigner à l’élément spécifié. Le type d' *élément* est défini par le TypeName *T* .

## <a name="vectorsize-method"></a><a name="size"></a> Vector :: Size, méthode

Retourne le nombre d'éléments dans l'objet Vector actuel.

### <a name="syntax"></a>Syntaxe

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments dans l’objet Vector actuel.

## <a name="vectorvector-constructor"></a><a name="ctor"></a> Vector :: Vector, constructeur

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

*un*<br/>
[Std :: Array](../standard-library/array-class-stl.md) qui sera utilisé pour initialiser le vecteur.

*arr*<br/>
[Plateforme :: Array](../cppcx/platform-array-class.md) qui sera utilisée pour initialiser le vecteur.

*Rein*<br/>
Type d’une collection d’objets utilisée pour initialiser l’objet Vector actuel.

*II*<br/>
[Std :: initializer_list](../standard-library/initializer-list-class.md) d’objets de type *T* qui seront utilisés pour initialiser le vecteur.

*N*<br/>
Nombre d’éléments d’une collection d’objets utilisée pour initialiser l’objet Vector actuel.

*size*<br/>
Nombre d'éléments dans l'objet Vector.

*value*<br/>
Valeur utilisée pour initialiser chaque élément de l'objet Vector actuel.

*v*<br/>
[Lvalues et rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) à un [std :: Vector](../standard-library/vector-class.md) utilisé pour initialiser le vecteur actuel.

*ptr*<br/>
Pointeur vers un `std::vector` utilisé pour initialiser l'objet Vector actuel.

*first*<br/>
Premier élément d'une séquence d'objets utilisée pour initialiser l'objet Vector actuel. Le type d' *abord* est passé au moyen d’un *transfert parfait*. Pour plus d'informations, consultez [Déclarateur de référence rvalue : &&](../cpp/rvalue-reference-declarator-amp-amp.md).

*last*<br/>
Dernier élément d'une séquence d'objets utilisée pour initialiser l'objet Vector actuel. Le type du *dernier* est passé au moyen d’un *transfert parfait*. Pour plus d'informations, consultez [Déclarateur de référence rvalue : &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Voir aussi

[Collections (C++/CX)](collections-c-cx.md)<br/>
[Espace de noms de plateforme](platform-namespace-c-cx.md)<br/>
[Création de composants Windows Runtime en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
