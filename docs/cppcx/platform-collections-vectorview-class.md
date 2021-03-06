---
description: 'En savoir plus sur : classe Platform :: Collections :: VectorView'
title: Platform::Collections::VectorView, classe
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorView::VectorView
- COLLECTION/Platform::Collections::VectorView::First
- COLLECTION/Platform::Collections::VectorView::GetAt
- COLLECTION/Platform::Collections::VectorView::GetMany
- COLLECTION/Platform::Collections::VectorView::IndexOf
- COLLECTION/Platform::Collections::VectorView::Size
helpviewer_keywords:
- VectorView Class
ms.assetid: 05cd461d-dce7-49d3-b0e7-2e5c78ed8192
ms.openlocfilehash: f0d1244ed5331fa9732bdfef1f1b7e2133f99442
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250034"
---
# <a name="platformcollectionsvectorview-class"></a>Platform::Collections::VectorView, classe

Représente une vue en lecture seule d'une collection d'objets séquentielle qui peut être accessible individuellement par index. Le type de chaque objet de la collection est défini par le paramètre de modèle.

## <a name="syntax"></a>Syntaxe

```
template <typename T, typename E>
   ref class VectorView sealed;
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type des éléments contenus dans l'objet `VectorView` .

*E*<br/>
Spécifie un prédicat binaire pour tester l'égalité des valeurs de type `T`. La valeur par défaut est `std::equal_to<T>`.

### <a name="remarks"></a>Notes

La `VectorView` classe implémente l’interface [Windows :: Foundation :: Collections :: \<T> IVectorView](/uwp/api/windows.foundation.collections.ivectorview-1) et la prise en charge des itérateurs de la bibliothèque STL (Standard Template Library).

### <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[VectorView :: VectorView](#ctor)|Initialise une nouvelle instance de la classe VectorView.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[VectorView :: First](#first)|Retourne un itérateur qui spécifie le premier élément du VectorView.|
|[VectorView :: GetAt](#getat)|Récupère l'élément du VectorView actuel qui est indiqué par l'index spécifié.|
|[VectorView :: Getmany (](#getmany)|Récupère une séquence d'éléments du VectorView actif en commençant à l'index spécifié.|
|[VectorView :: IndexOf](#indexof)|Recherche l'élément spécifié dans l'objet VectorView actuel, et s'il existe, retourne l'index de l'élément.|
|[VectorView::Size](#size)|Retourne le nombre d'éléments dans l'objet VectorView actuel.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`VectorView`

### <a name="requirements"></a>Spécifications

**En-tête :** collection.h

**Espace de noms :** Platform::Collections

## <a name="vectorviewfirst-method"></a><a name="first"></a> VectorView :: First, méthode

Retourne un itérateur qui spécifie le premier élément du VectorView.

### <a name="syntax"></a>Syntaxe

```

virtual Windows::Foundation::Collections::IIterator<T>^
   First();
```

### <a name="return-value"></a>Valeur de retour

Itérateur qui spécifie le premier élément de l'objet VectorView.

### <a name="remarks"></a>Notes

Un moyen pratique de contenir l’itérateur retourné par First () consiste à affecter la valeur de retour à une variable déclarée avec le **`auto`** mot clé de déduction de type. Par exemple, `auto x = myVectorView->First();`.

## <a name="vectorviewgetat-method"></a><a name="getat"></a> VectorView :: GetAt, méthode

Récupère l'élément du VectorView actuel qui est indiqué par l'index spécifié.

### <a name="syntax"></a>Syntaxe

```

T GetAt(
   UInt32 index
);
```

### <a name="parameters"></a>Paramètres

*index*<br/>
Entier non signé de base zéro qui spécifie un élément particulier dans l’objet VectorView.

### <a name="return-value"></a>Valeur renvoyée

Élément spécifié par le paramètre `index`. Le type d’élément est spécifié par le paramètre de modèle VectorView, *T*.

## <a name="vectorviewgetmany-method"></a><a name="getmany"></a> VectorView :: Getmany (, méthode

Récupère une séquence d'éléments du VectorView actif en commençant à l'index spécifié.

### <a name="syntax"></a>Syntaxe

```

virtual unsigned int GetMany(
   unsigned int startIndex,
   ::Platform::WriteOnlyArray<T>^ dest
);
```

### <a name="parameters"></a>Paramètres

*startIndex*<br/>
L'index de base zéro du début des éléments à récupérer.

*dest*<br/>
Quand cette opération se termine, un tableau d’éléments qui commencent à l’élément spécifié par `startIndex` et se terminent au dernier élément du VectorView.

### <a name="return-value"></a>Valeur renvoyée

Le nombre d'éléments à récupérer.

## <a name="vectorviewindexof-method"></a><a name="indexof"></a> VectorView :: IndexOf, méthode

Recherche l'élément spécifié dans l'objet VectorView actuel, et s'il existe, retourne l'index de l'élément.

### <a name="syntax"></a>Syntaxe

```

virtual bool IndexOf(
   T value,
   unsigned int* index
);
```

### <a name="parameters"></a>Paramètres

*value*<br/>
Élément à rechercher.

*index*<br/>
Index de base zéro de l'élément si le paramètre `value` est détecté ; sinon, 0.

Le paramètre d' *index* est 0 si l’élément est le premier élément du `VectorView` ou si l’élément est introuvable. Si la valeur de retour est **`true`** , l’élément a été trouvé et il s’agit du premier élément ; sinon, l’élément est introuvable.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l’élément spécifié est trouvé ; Sinon, **`false`** .

## <a name="vectorviewsize-method"></a><a name="size"></a> VectorView :: Size, méthode

Retourne le nombre d'éléments dans l'objet VectorView actuel.

### <a name="syntax"></a>Syntaxe

```

virtual property unsigned int Size;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments dans le VectorView actuel.

## <a name="vectorviewvectorview-constructor"></a><a name="ctor"></a> VectorView :: VectorView, constructeur

Initialise une nouvelle instance de la classe VectorView.

### <a name="syntax"></a>Syntaxe

```
VectorView();
explicit VectorView(
   UInt32 size
);
VectorView(
   UInt32 size,
   T value
);
explicit VectorView(
   const ::std::vector<T>& v
);
explicit VectorView(
   ::std::vector<T>&& v
);
VectorView(
   const T * ptr,
   UInt32 size
);

template <
   size_t N
>
explicit VectorView(
   const T (&arr)[N]
);

template <
   size_t N
>
explicit VectorView(
   const ::std::array<T,
   N>& a
);

explicit VectorView(
   const ::Platform::Array<T>^ arr
);

template <
   typename InIt
>
VectorView(
   InItfirst,
   InItlast
);

VectorView(
   std::initializer_list<T> il
);
```

### <a name="parameters"></a>Paramètres

*Rein*<br/>
Type d’une collection d’objets utilisée pour initialiser le VectorView actif.

*II*<br/>
[Std :: initializer_list](../standard-library/initializer-list-class.md) dont les éléments sont utilisés pour initialiser le vectorview.

*N*<br/>
Nombre d’éléments d’une collection d’objets utilisée pour initialiser le VectorView actif.

*size*<br/>
Nombre d'éléments du VectorView.

*value*<br/>
Valeur utilisée pour initialiser chaque élément du VectorView actif.

*v*<br/>
[Lvalues et rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) à un [std :: Vector](../standard-library/vector-class.md) utilisé pour initialiser le vectorview actuel.

*ptr*<br/>
Pointeur vers un `std::vector` utilisé pour initialiser le VectorView actif.

*arr*<br/>
Objet [Platform :: Array](../cppcx/platform-array-class.md) utilisé pour initialiser le vectorview actif.

*un*<br/>
Objet [std :: Array](../standard-library/array-class-stl.md) utilisé pour initialiser le vectorview actif.

*first*<br/>
Premier élément d'une séquence d'objets utilisée pour initialiser le VectorView actif. Le type de `first` est passé au moyen d’un *transfert parfait*. Pour plus d'informations, consultez [Déclarateur de référence rvalue : &&](../cpp/rvalue-reference-declarator-amp-amp.md).

*last*<br/>
Dernier élément d'une séquence d'objets utilisée pour initialiser le VectorView actif. Le type de `last` est passé au moyen d’un *transfert parfait*. Pour plus d'informations, consultez [Déclarateur de référence rvalue : &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Voir aussi

[Espace de noms de plateforme](platform-namespace-c-cx.md)<br/>
[Création de composants Windows Runtime en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
