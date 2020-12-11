---
description: 'En savoir plus sur : classe CAdapt'
title: CAdapt, classe
ms.date: 11/04/2016
f1_keywords:
- CAdapt
- ATLCOMCLI/ATL::CAdapt
- ATLCOMCLI/ATL::CAdapt::CAdapt
- ATLCOMCLI/ATL::CAdapt::m_T
helpviewer_keywords:
- address-of operator
- adapter objects
- '& operator, address-of operator'
- CAdapt class
ms.assetid: 0bb695a5-72fe-43d1-8f39-7e4da6e34765
ms.openlocfilehash: 6c6ec1c40d430c2de64defb5ea7394a47b1d7a6f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158502"
---
# <a name="cadapt-class"></a>CAdapt, classe

Ce modèle permet d'inclure dans un wrapper les classes qui redéfinissent l'opérateur d'adresse afin de retourner un autre élément que l'adresse de l'objet.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class CAdapt
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type adapté.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAdapt::CAdapt](#cadapt)|Constructeur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAdapt :: Operator const T&](#operator_const_t_amp)|Retourne une **`const`** référence à `m_T` .|
|[CAdapt :: Operator T&](#operator_t_amp)|Retourne une référence à `m_T`.|
|[CAdapt :: Operator <](#operator_lt)|Compare un objet du type adapté à `m_T`.|
|[CAdapt :: Operator =](#operator_eq)|Assigne un objet du type adapté à `m_T`.|
|[CAdapt :: Operator = =](#operator_eq_eq)|Compare un objet du type adapté à `m_T`.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAdapt :: m_T](#m_t)|Données adaptées.|

## <a name="remarks"></a>Notes

`CAdapt` est un modèle simple qui permet d'inclure dans un wrapper les classes qui redéfinissent l'opérateur d'adresse (`operator &`) afin de retourner un autre élément que l'adresse de l'objet. Parmi ces exemples de classes figurent les classes ATL `CComBSTR`, `CComPtr` et `CComQIPtr`, ainsi que la classe de prise en charge COM du compilateur, `_com_ptr_t`. Ces classes redéfinissent l’opérateur d’adresse pour retourner l’adresse de l’un de leurs membres de données (un BSTR dans le cas de `CComBSTR` , et un pointeur d’interface dans le cas des autres classes).

`CAdapt`le rôle principal de est de masquer l’opérateur d’adresse défini par la classe *T*, tout en conservant les caractéristiques de la classe adaptée. `CAdapt` remplit ce rôle en détenant un membre public, [m_T](#m_t), de type *T* et en définissant des opérateurs de conversion, des opérateurs de comparaison et un constructeur de copie pour permettre aux spécialisations de d' `CAdapt` être traitées comme s’il s’agissait d’objets de type *T*.

La classe d'adaptateur `CAdapt` est utile, car certaines classes de type conteneur sont censées être capables d'obtenir les adresses des objets contenus via l'opérateur d'adresse. La redéfinition de l’opérateur d’adresse peut confondre cette exigence, généralement en provoquant des erreurs de compilation et en empêchant l’utilisation du type non adapté avec les classes qui s’attendent à ce qu’il fonctionne « tout simplement ». `CAdapt` permet de contourner ces problèmes.

En règle générale, utilisez `CAdapt` lorsque vous souhaitez stocker des objets `CComBSTR`, `CComPtr`, `CComQIPtr` ou `_com_ptr_t` dans une classe de type conteneur. Ceci était le plus souvent nécessaire pour les conteneurs de bibliothèque standard C++ avant la prise en charge de la norme C++11. Toutefois, les conteneurs de bibliothèque standard C++11 fonctionnent automatiquement avec les types ayant un `operator&()` surchargé. La bibliothèque standard réalise cela en interne à l’aide de [std :: AddressOf](../../standard-library/memory-functions.md#addressof) pour obtenir les véritables adresses d’objets.

## <a name="requirements"></a>Spécifications

**En-tête :** atlcomcli. h

## <a name="cadaptcadapt"></a><a name="cadapt"></a> CAdapt::CAdapt

Les constructeurs permettent à un objet d’adaptateur d’être construit par défaut, copié à partir d’un objet du type adapté, ou copié à partir d’un autre objet adaptateur.

```cpp
CAdapt();
CAdapt(const T& rSrc);
CAdapt(const CAdapt& rSrCA);
CAdapt(T&& rSrCA);  // (Visual Studio 2017)
CAdapt(CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Paramètres

*rSrc*<br/>
Variable du type qui est adaptée pour être copiée dans l’objet adaptateur nouvellement construit.

*rSrCA*<br/>
Objet adaptateur dont les données contenues doivent être copiées (ou déplacées) dans l’objet adaptateur nouvellement construit.

## <a name="cadaptm_t"></a><a name="m_t"></a> CAdapt :: m_T

Contient les données en cours d’adaptation.

```cpp
T m_T;
```

### <a name="remarks"></a>Notes

Ce **`public`** membre de données est accessible directement ou indirectement avec l' [opérateur const t&](#operator_const_t_amp) et l' [opérateur t&](#operator_t_amp).

## <a name="cadaptoperator-const-tamp"></a><a name="operator_const_t_amp"></a> CAdapt :: Operator const T&amp;

Retourne une **`const`** référence au membre [m_T](#m_t) , ce qui permet de traiter l’objet d’adaptateur comme s’il s’agissait d’un objet de type *T*.

```cpp
operator const T&() const;
```

### <a name="return-value"></a>Valeur renvoyée

**`const`** Référence à `m_T` .

## <a name="cadaptoperator-tamp"></a><a name="operator_t_amp"></a> CAdapt :: Operator T&amp;

Retourne une référence au membre [m_T](#m_t) , ce qui permet de traiter l’objet d’adaptateur comme s’il s’agissait d’un objet de type *T*.

```cpp
operator T&();
```

### <a name="return-value"></a>Valeur renvoyée

Référence à `m_T`.

## <a name="cadaptoperator-lt"></a><a name="operator_lt"></a> CAdapt ::, opérateur &lt;

Compare un objet du type adapté à [m_T](#m_t).

```cpp
bool operator<(const T& rSrc) const;
```

### <a name="parameters"></a>Paramètres

*rSrc*<br/>
Référence à l’objet à comparer.

### <a name="return-value"></a>Valeur renvoyée

Résultat de la comparaison entre `m_T` et *rSrc*.

## <a name="cadaptoperator-"></a><a name="operator_eq"></a> CAdapt :: Operator =

L’opérateur d’assignation assigne l’argument, *rSrc*, au membre de données [m_T](#m_t) et retourne l’objet d’adaptateur actuel.

```cpp
CAdapt& operator= (const T& rSrc);
CAdapt& operator= (T&& rSrCA); // (Visual Studio 2017)
CAdapt& operator= (CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Paramètres

*rSrc*<br/>
Référence à un objet du type adapté à copier.

*rSrCA*<br/>
Référence à un objet à déplacer.

### <a name="return-value"></a>Valeur renvoyée

Référence à l’objet actuel.

## <a name="cadaptoperator-"></a><a name="operator_eq_eq"></a> CAdapt :: Operator = =

Compare un objet du type adapté à [m_T](#m_t).

```cpp
bool operator== (const T& rSrc) const;
```

### <a name="parameters"></a>Paramètres

*rSrc*<br/>
Référence à l’objet à comparer.

### <a name="return-value"></a>Valeur renvoyée

Résultat de la comparaison entre *m_T* et *rSrc*.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
