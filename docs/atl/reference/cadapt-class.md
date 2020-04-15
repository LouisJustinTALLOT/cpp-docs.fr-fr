---
title: Classe CAdapt
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
ms.openlocfilehash: 23544bc103de0d7b76cd73d403626ba93af6e31a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321642"
---
# <a name="cadapt-class"></a>Classe CAdapt

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
|[CAdapt::opérateur const T&](#operator_const_t_amp)|Retourne une référence `m_T` **const** à .|
|[CAdapt::opérateur T&](#operator_t_amp)|Retourne une référence à `m_T`.|
|[CAdapt::opérateur <](#operator_lt)|Compare un objet du type adapté à `m_T`.|
|[CAdapt::opérateur](#operator_eq)|Assigne un objet du type adapté à `m_T`.|
|[CAdapt::opérateur](#operator_eq_eq)|Compare un objet du type adapté à `m_T`.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAdapt::m_T](#m_t)|Données adaptées.|

## <a name="remarks"></a>Notes

`CAdapt` est un modèle simple qui permet d'inclure dans un wrapper les classes qui redéfinissent l'opérateur d'adresse (`operator &`) afin de retourner un autre élément que l'adresse de l'objet. Parmi ces exemples de classes figurent les classes ATL `CComBSTR`, `CComPtr` et `CComQIPtr`, ainsi que la classe de prise en charge COM du compilateur, `_com_ptr_t`. Ces classes redéfinissent toutes l’adresse de l’opérateur pour retourner l’adresse d’un de leurs membres de données (un BSTR dans le cas de `CComBSTR`, et un pointeur d’interface dans le cas des autres classes).

`CAdapt`le rôle principal est de masquer l’adresse de l’opérateur défini par la classe *T,* tout en conservant les caractéristiques de la classe adaptée. `CAdapt`remplit ce rôle en tenant un membre public, [m_T](#m_t), de type *T*, et en définissant les opérateurs `CAdapt` de conversion, les opérateurs de comparaison, et un constructeur de copie pour permettre des spécialisations de à traiter comme s’ils étaient des objets de type *T*.

La classe d'adaptateur `CAdapt` est utile, car certaines classes de type conteneur sont censées être capables d'obtenir les adresses des objets contenus via l'opérateur d'adresse. La redéfinition de l’opérateur d’adresse peut confondre cette exigence, généralement en provoquant des erreurs de compilation et en empêchant l’utilisation du type non adapté avec les classes qui s’attendent à ce qu’il fonctionne « tout simplement ». `CAdapt` permet de contourner ces problèmes.

En règle générale, utilisez `CAdapt` lorsque vous souhaitez stocker des objets `CComBSTR`, `CComPtr`, `CComQIPtr` ou `_com_ptr_t` dans une classe de type conteneur. Ceci était le plus souvent nécessaire pour les conteneurs de bibliothèque standard C++ avant la prise en charge de la norme C++11. Toutefois, les conteneurs de bibliothèque standard C++11 fonctionnent automatiquement avec les types ayant un `operator&()` surchargé. La Bibliothèque Standard y parvient en utilisant en interne [std::adresse](../../standard-library/memory-functions.md#addressof) pour obtenir les vraies adresses des objets.

## <a name="requirements"></a>Spécifications

**En-tête:** atlcomcli.h

## <a name="cadaptcadapt"></a><a name="cadapt"></a>CAdapt::CAdapt

Les constructeurs permettent à un objet adaptateur d’être construit par défaut, copié à partir d’un objet du type adapté, ou copié à partir d’un autre objet adaptateur.

```
CAdapt();
CAdapt(const T& rSrc);
CAdapt(const CAdapt& rSrCA);
CAdapt(T&& rSrCA);  // (Visual Studio 2017)
CAdapt(CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Paramètres

*rSrc (rSrc)*<br/>
Une variable du type adaptée pour être copiée dans l’objet adaptateur nouvellement construit.

*rSrCA (RSrCA)*<br/>
Un objet adaptateur dont les données contenues doivent être copiées (ou déplacées) dans l’objet adaptateur nouvellement construit.

## <a name="cadaptm_t"></a><a name="m_t"></a>CAdapt::m_T

Maintient les données en cours d’adaptation.

```
T m_T;
```

### <a name="remarks"></a>Notes

Ce membre **public** des données peut être consulté directement ou indirectement avec [l’opérateur const T&](#operator_const_t_amp) et [l’opérateur T&](#operator_t_amp).

## <a name="cadaptoperator-const-tamp"></a><a name="operator_const_t_amp"></a>CAdapt::opérateur const T&amp;

Renvoie une référence **const** au [membre m_T,](#m_t) permettant à l’objet adaptateur d’être traité comme s’il s’agissait d’un objet de type *T*.

```
operator const T&() const;
```

### <a name="return-value"></a>Valeur de retour

Une référence **const** à `m_T`.

## <a name="cadaptoperator-tamp"></a><a name="operator_t_amp"></a>CAdapt::opérateur T&amp;

Renvoie une référence au [membre m_T,](#m_t) permettant à l’objet adaptateur d’être traité comme s’il s’agissait d’un objet de type *T*.

```
operator T&();
```

### <a name="return-value"></a>Valeur de retour

Référence à `m_T`.

## <a name="cadaptoperator-lt"></a><a name="operator_lt"></a>CAdapt::opérateur&lt;

Compare un objet du type adapté avec [m_T](#m_t).

```
bool operator<(const T& rSrc) const;
```

### <a name="parameters"></a>Paramètres

*rSrc (rSrc)*<br/>
Une référence à l’objet à comparer.

### <a name="return-value"></a>Valeur de retour

Le résultat de `m_T` la comparaison entre et *rSrc*.

## <a name="cadaptoperator-"></a><a name="operator_eq"></a>CAdapt::opérateur

L’opérateur d’affectation assigne l’argument, *rSrc*, au membre de données [m_T](#m_t) et renvoie l’objet adaptateur actuel.

```
CAdapt& operator= (const T& rSrc);
CAdapt& operator= (T&& rSrCA); // (Visual Studio 2017)
CAdapt& operator= (CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Paramètres

*rSrc (rSrc)*<br/>
Une référence à un objet du type adapté à copier.

*rSrCA (RSrCA)*<br/>
Une référence à un objet à déplacer.

### <a name="return-value"></a>Valeur de retour

Une référence à l’objet actuel.

## <a name="cadaptoperator-"></a><a name="operator_eq_eq"></a>CAdapt::opérateur

Compare un objet du type adapté avec [m_T](#m_t).

```
bool operator== (const T& rSrc) const;
```

### <a name="parameters"></a>Paramètres

*rSrc (rSrc)*<br/>
Une référence à l’objet à comparer.

### <a name="return-value"></a>Valeur de retour

Le résultat de la comparaison entre *m_T* et *rSrc*.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
