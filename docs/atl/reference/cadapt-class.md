---
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
ms.openlocfilehash: 39184e952475fa0f05a6fc25c433191ea22b5c16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260738"
---
# <a name="cadapt-class"></a>CAdapt, classe

Ce modèle permet d'inclure dans un wrapper les classes qui redéfinissent l'opérateur d'adresse afin de retourner un autre élément que l'adresse de l'objet.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class CAdapt
```

#### <a name="parameters"></a>Paramètres

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
|[CAdapt::operator const T &](#operator_const_t_amp)|Retourne un **const** référence à `m_T`.|
|[CAdapt::operator T &](#operator_t_amp)|Retourne une référence à `m_T`.|
|[CAdapt::operator <](#operator_lt)|Compare un objet du type adapté à `m_T`.|
|[CAdapt::operator =](#operator_eq)|Assigne un objet du type adapté à `m_T`.|
|[CAdapt::operator ==](#operator_eq_eq)|Compare un objet du type adapté à `m_T`.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAdapt::m_T](#m_t)|Données adaptées.|

## <a name="remarks"></a>Notes

`CAdapt` est un modèle simple qui permet d'inclure dans un wrapper les classes qui redéfinissent l'opérateur d'adresse (`operator &`) afin de retourner un autre élément que l'adresse de l'objet. Parmi ces exemples de classes figurent les classes ATL `CComBSTR`, `CComPtr` et `CComQIPtr`, ainsi que la classe de prise en charge COM du compilateur, `_com_ptr_t`. Ces classes redéfinissent toutes l’opérateur address-of pour retourner l’adresse de l’un de leurs membres de données (un BSTR dans le cas de `CComBSTR`et un pointeur d’interface dans le cas d’autres classes).

`CAdapt`du rôle principal est de masquer l’opérateur address-of définie par la classe *T*, tout en conservant les caractéristiques de la classe adaptée. `CAdapt` remplit ce rôle en détenant un membre public, [m_T](#m_t), de type *T*et en définissant des opérateurs de conversion, opérateurs de comparaison et un constructeur de copie pour autoriser les spécialisations de `CAdapt` être traitée comme si elles sont des objets de type *T*.

La classe d'adaptateur `CAdapt` est utile, car certaines classes de type conteneur sont censées être capables d'obtenir les adresses des objets contenus via l'opérateur d'adresse. La redéfinition de l’opérateur d’adresse peut confondre cette exigence, généralement en provoquant des erreurs de compilation et en empêchant l’utilisation du type non adapté avec les classes qui s’attendent à ce qu’il fonctionne « tout simplement ». `CAdapt` permet de contourner ces problèmes.

En règle générale, utilisez `CAdapt` lorsque vous souhaitez stocker des objets `CComBSTR`, `CComPtr`, `CComQIPtr` ou `_com_ptr_t` dans une classe de type conteneur. Ceci était le plus souvent nécessaire pour les conteneurs de bibliothèque standard C++ avant la prise en charge de la norme C++11. Toutefois, les conteneurs de bibliothèque standard C++11 fonctionnent automatiquement avec les types ayant un `operator&()` surchargé. La bibliothèque Standard pour cela en interne à l’aide de [std::addressof](../../standard-library/memory-functions.md#addressof) pour obtenir les adresses réelles des objets.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcomcli.h

##  <a name="cadapt"></a>  CAdapt::CAdapt

Les constructeurs permettent à un objet d’adaptateur comme valeur par défaut construit, copié à partir d’un objet du type adapté ou copiés à partir d’un autre objet de carte.

```
CAdapt();
CAdapt(const T& rSrc);
CAdapt(const CAdapt& rSrCA);
CAdapt(T&& rSrCA);  // (Visual Studio 2017)
CAdapt(CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Paramètres

*rSrc*<br/>
Une variable du type qui est adapté pour être copié dans l’objet d’adaptateur nouvellement construit.

*rSrCA*<br/>
Un objet d’adaptateur dont les données relation contenant-contenues doivent copier (ou à déplacer) dans l’objet d’adaptateur nouvellement construit.

##  <a name="m_t"></a>  CAdapt::m_T

Contient les données qui est adaptées.

```
T m_T;
```

### <a name="remarks"></a>Notes

Cela **public** membre de données est accessible directement ou indirectement avec [opérateur const T &](#operator_const_t_amp) et [opérateur T &](#operator_t_amp).

##  <a name="operator_const_t_amp"></a>  CAdapt::operator const T&amp;

Retourne un **const** font référence à la [m_T](#m_t) membre, permettant ainsi l’objet d’adaptateur être traité comme s’il s’agissait d’un objet de type *T*.

```
operator const T&() const;
```

### <a name="return-value"></a>Valeur de retour

Un **const** référence à `m_T`.

##  <a name="operator_t_amp"></a>  CAdapt::operator T&amp;

Retourne une référence à la [m_T](#m_t) membre, permettant ainsi l’objet d’adaptateur être traité comme s’il s’agissait d’un objet de type *T*.

```
operator T&();
```

### <a name="return-value"></a>Valeur de retour

Une référence à `m_T`.

##  <a name="operator_lt"></a>  CAdapt::operator &lt;

Compare un objet du type adapté à [m_T](#m_t).

```
bool operator<(const T& rSrc) const;
```

### <a name="parameters"></a>Paramètres

*rSrc*<br/>
Une référence à l’objet à comparer.

### <a name="return-value"></a>Valeur de retour

Le résultat de la comparaison entre `m_T` et *rSrc*.

##  <a name="operator_eq"></a>  CAdapt::operator =

L’opérateur d’assignation assigne l’argument, *rSrc*, pour le membre de données [m_T](#m_t) et retourne l’objet en cours de la carte.

```
CAdapt& operator= (const T& rSrc);
CAdapt& operator= (T&& rSrCA); // (Visual Studio 2017)
CAdapt& operator= (CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Paramètres

*rSrc*<br/>
Une référence à un objet du type adapté à copier.

*rSrCA*<br/>
Une référence à un objet à déplacer.

### <a name="return-value"></a>Valeur de retour

Une référence à l’objet actuel.

##  <a name="operator_eq_eq"></a>  CAdapt::operator ==

Compare un objet du type adapté à [m_T](#m_t).

```
bool operator== (const T& rSrc) const;
```

### <a name="parameters"></a>Paramètres

*rSrc*<br/>
Une référence à l’objet à comparer.

### <a name="return-value"></a>Valeur de retour

Le résultat de la comparaison entre *m_T* et *rSrc*.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
