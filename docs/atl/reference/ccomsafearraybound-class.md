---
title: CComSafeArrayBound, classe
ms.date: 05/06/2019
f1_keywords:
- CComSafeArrayBound
- ATLSAFE/ATL::CComSafeArrayBound
- ATLSAFE/ATL::GetCount
- ATLSAFE/ATL::GetLowerBound
- ATLSAFE/ATL::GetUpperBound
- ATLSAFE/ATL::SetCount
- ATLSAFE/ATL::SetLowerBound
helpviewer_keywords:
- CComSafeArrayBound class
ms.assetid: dd6299db-5f84-4630-bbf0-f5add5318437
ms.openlocfilehash: 9adee1e8b6a46c239aaf6a3c404277b34efd00e2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834750"
---
# <a name="ccomsafearraybound-class"></a>CComSafeArrayBound, classe

Cette classe est un wrapper pour une structure [SAFEARRAYBOUND](/windows/win32/api/oaidl/ns-oaidl-safearraybound) .

## <a name="syntax"></a>Syntaxe

```
class CComSafeArrayBound : public SAFEARRAYBOUND
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|Fonction|Description|
|-|-|
|[CComSafeArrayBound](#ccomsafearraybound)|Constructeur.|
|[GetCount](#getcount)|Appelez cette méthode pour retourner le nombre d’éléments.|
|[GetLowerBound](#getlowerbound)|Appelez cette méthode pour retourner la limite inférieure.|
|[GetUpperBound](#getupperbound)|Appelez cette méthode pour retourner la limite supérieure.|
|[SetCount](#setcount)|Appelez cette méthode pour définir le nombre d’éléments.|
|[SetLowerBound](#setlowerbound)|Appelez cette méthode pour définir la limite inférieure.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur =](#operator_eq)|Affecte `CComSafeArrayBound` une nouvelle valeur à.|

## <a name="remarks"></a>Notes

Cette classe est un wrapper pour la `SAFEARRAYBOUND` structure utilisée par [CComSafeArray](../../atl/reference/ccomsafearray-class.md). Il fournit des méthodes pour interroger et définir les limites supérieure et inférieure d’une dimension unique d’un `CComSafeArray` objet et le nombre d’éléments qu’elle contient. Un objet multidimensionnel `CComSafeArray` utilise un tableau d' `CComSafeArrayBound` objets, un pour chaque dimension. Par conséquent, lorsque vous utilisez des méthodes telles que [GetCount](#getcount), sachez que cette méthode ne retourne pas le nombre total d’éléments dans un tableau multidimensionnel.

**En-tête :** atlsafe.h

## <a name="requirements"></a>Configuration requise

**En-tête :** atlsafe.h

## <a name="ccomsafearrayboundccomsafearraybound"></a><a name="ccomsafearraybound"></a> CComSafeArrayBound::CComSafeArrayBound

Constructeur.

```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```

### <a name="parameters"></a>Paramètres

*ulCount*<br/>
Nombre d’éléments dans le tableau.

*lLowerBound*<br/>
Limite inférieure de laquelle le tableau est numéroté.

### <a name="remarks"></a>Notes

Si le tableau doit être accessible à partir d’un programme C++, il est recommandé de définir la limite inférieure sur 0. Il peut être préférable d’utiliser une autre valeur de limite inférieure si le tableau doit être utilisé avec d’autres langages, tels que Visual Basic.

## <a name="ccomsafearrayboundgetcount"></a><a name="getcount"></a> CComSafeArrayBound :: GetCount

Appelez cette méthode pour retourner le nombre d’éléments.

```
ULONG GetCount() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre d’éléments.

### <a name="remarks"></a>Notes

Si l' `CComSafeArray` objet associé représente un tableau multidimensionnel, cette méthode retourne uniquement le nombre total d’éléments dans la dimension la plus à droite. Utilisez [CComSafeArray :: GetCount](../../atl/reference/ccomsafearray-class.md#getcount) pour obtenir le nombre total d’éléments.

## <a name="ccomsafearrayboundgetlowerbound"></a><a name="getlowerbound"></a> CComSafeArrayBound::GetLowerBound

Appelez cette méthode pour retourner la limite inférieure.

```
LONG GetLowerBound() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la limite inférieure de l' `CComSafeArrayBound` objet.

## <a name="ccomsafearrayboundgetupperbound"></a><a name="getupperbound"></a> CComSafeArrayBound :: GetUpperBound

Appelez cette méthode pour retourner la limite supérieure.

```
LONG GetUpperBound() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la limite supérieure de l' `CComSafeArrayBound` objet.

### <a name="remarks"></a>Notes

La limite supérieure dépend du nombre d’éléments et de la valeur limite inférieure. Par exemple, si la limite inférieure est 0 et que le nombre d’éléments est 10, la limite supérieure sera automatiquement définie sur 9.

## <a name="ccomsafearrayboundoperator-"></a><a name="operator_eq"></a> CComSafeArrayBound :: Operator =

Affecte `CComSafeArrayBound` une nouvelle valeur à.

```
CComSafeArrayBound& operator= (const CComSafeArrayBound& bound) throw();
CComSafeArrayBound& operator= (ULONG ulCount) throw();
```

### <a name="parameters"></a>Paramètres

*indépendantes*<br/>
Objet `CComSafeArrayBound`.

*ulCount*<br/>
Nombre d'éléments.

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers l' `CComSafeArrayBound` objet.

### <a name="remarks"></a>Notes

L' `CComSafeArrayBound` objet peut être assigné à l’aide d’un existant `CComSafeArrayBound` ou en fournissant le nombre d’éléments, auquel cas la limite inférieure est définie sur 0 par défaut.

## <a name="ccomsafearrayboundsetcount"></a><a name="setcount"></a> CComSafeArrayBound::SetCount

Appelez cette méthode pour définir le nombre d’éléments.

```
ULONG SetCount(ULONG ulCount) throw();
```

### <a name="parameters"></a>Paramètres

*ulCount*<br/>
Nombre d'éléments.

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre d’éléments dans l' `CComSafeArrayBound` objet.

## <a name="ccomsafearrayboundsetlowerbound"></a><a name="setlowerbound"></a> CComSafeArrayBound::SetLowerBound

Appelez cette méthode pour définir la limite inférieure.

```
LONG SetLowerBound(LONG lLowerBound) throw();
```

### <a name="parameters"></a>Paramètres

*lLowerBound*<br/>
Limite inférieure.

### <a name="return-value"></a>Valeur renvoyée

Retourne la nouvelle limite inférieure de l' `CComSafeArrayBound` objet.

### <a name="remarks"></a>Notes

Si le tableau doit être accessible à partir d’un programme Visual C++, il est recommandé de définir la limite inférieure sur 0. Il peut être préférable d’utiliser une autre valeur de limite inférieure si le tableau doit être utilisé avec d’autres langages, tels que Visual Basic.

La limite supérieure dépend du nombre d’éléments et de la valeur limite inférieure. Par exemple, si la limite inférieure est 0 et que le nombre d’éléments est 10, la limite supérieure sera automatiquement définie sur 9.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
