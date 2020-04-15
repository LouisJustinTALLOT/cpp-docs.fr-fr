---
title: Classe CComSafeArrayBound
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
ms.openlocfilehash: 2c2f8b787e5366ec893538a88049f6f53dc35caf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327379"
---
# <a name="ccomsafearraybound-class"></a>Classe CComSafeArrayBound

Cette classe est un emballage pour une structure [SAFEARRAYBOUND.](/windows/win32/api/oaidl/ns-oaidl-safearraybound)

## <a name="syntax"></a>Syntaxe

```
class CComSafeArrayBound : public SAFEARRAYBOUND
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[CComSafeArrayBound](#ccomsafearraybound)|Constructeur.|
|[GetCount](#getcount)|Appelez cette méthode pour retourner le nombre d’éléments.|
|[GetLowerBound (en)](#getlowerbound)|Appelez cette méthode pour retourner la limite inférieure.|
|[GetUpperBound (en)](#getupperbound)|Appelez cette méthode pour retourner la limite supérieure.|
|[SetCount (en)](#setcount)|Appelez cette méthode pour définir le nombre d’éléments.|
|[SetLowerBound (en)](#setlowerbound)|Appelez cette méthode pour définir la limite inférieure.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[opérateur](#operator_eq)|Définit `CComSafeArrayBound` la valeur à une nouvelle valeur.|

## <a name="remarks"></a>Notes

Cette classe est un `SAFEARRAYBOUND` emballage pour la structure utilisée par [CComSafeArray](../../atl/reference/ccomsafearray-class.md). Il fournit des méthodes pour interroger et définir les limites `CComSafeArray` supérieures et inférieures d’une seule dimension d’un objet et le nombre d’éléments qu’il contient. Un objet `CComSafeArray` multidimensionnel utilise `CComSafeArrayBound` une gamme d’objets, un pour chaque dimension. Par conséquent, lors de l’utilisation de méthodes telles que [GetCount](#getcount), sachez que cette méthode ne retournera pas le nombre total d’éléments dans un tableau multidimensionnel.

**En-tête :** atlsafe.h

## <a name="requirements"></a>Spécifications

**En-tête :** atlsafe.h

## <a name="ccomsafearrayboundccomsafearraybound"></a><a name="ccomsafearraybound"></a>CComSafeArrayBound::CComSafeArrayBound

Constructeur.

```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```

### <a name="parameters"></a>Paramètres

*ulCount ulCount*<br/>
Nombre d’éléments dans le tableau.

*lLowerBound (en)*<br/>
La limite inférieure à partir de laquelle le tableau est numéroté.

### <a name="remarks"></a>Notes

Si le tableau doit être accessible à partir d’un programme C, il est recommandé que la limite inférieure soit définie comme 0. Il peut être préférable d’utiliser une valeur limite inférieure différente si le tableau doit être utilisé avec d’autres langues, telles que Visual Basic.

## <a name="ccomsafearrayboundgetcount"></a><a name="getcount"></a>CComSafeArrayBound::GetCount

Appelez cette méthode pour retourner le nombre d’éléments.

```
ULONG GetCount() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’éléments.

### <a name="remarks"></a>Notes

Si l’objet associé `CComSafeArray` représente un tableau multidimensionnel, cette méthode ne retournera que le nombre total d’éléments dans la dimension la plus droite. Utilisez [CComSafeArray::GetCount](../../atl/reference/ccomsafearray-class.md#getcount) pour obtenir le nombre total d’éléments.

## <a name="ccomsafearrayboundgetlowerbound"></a><a name="getlowerbound"></a>CComSafeArrayBound::GetLowerBound

Appelez cette méthode pour retourner la limite inférieure.

```
LONG GetLowerBound() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la limite `CComSafeArrayBound` inférieure de l’objet.

## <a name="ccomsafearrayboundgetupperbound"></a><a name="getupperbound"></a>CComSafeArrayBound::GetUpperBound

Appelez cette méthode pour retourner la limite supérieure.

```
LONG GetUpperBound() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la limite `CComSafeArrayBound` supérieure de l’objet.

### <a name="remarks"></a>Notes

La limite supérieure dépend du nombre d’éléments et de la valeur inférieure. Par exemple, si la limite inférieure est de 0 et que le nombre d’éléments est de 10, la limite supérieure sera automatiquement réglée à 9.

## <a name="ccomsafearrayboundoperator-"></a><a name="operator_eq"></a>CComSafeArrayBound::opérateur

Définit `CComSafeArrayBound` la valeur à une nouvelle valeur.

```
CComSafeArrayBound& operator= (const CComSafeArrayBound& bound) throw();
CComSafeArrayBound& operator= (ULONG ulCount) throw();
```

### <a name="parameters"></a>Paramètres

*Lié*<br/>
Objet `CComSafeArrayBound` .

*ulCount ulCount*<br/>
Nombre d'éléments.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur à l’objet. `CComSafeArrayBound`

### <a name="remarks"></a>Notes

L’objet `CComSafeArrayBound` peut être `CComSafeArrayBound`assigné à l’aide d’un existant, ou en fournissant le nombre d’éléments, auquel cas la limite inférieure est réglée à 0 par défaut.

## <a name="ccomsafearrayboundsetcount"></a><a name="setcount"></a>CComSafeArrayBound::SetCount

Appelez cette méthode pour définir le nombre d’éléments.

```
ULONG SetCount(ULONG ulCount) throw();
```

### <a name="parameters"></a>Paramètres

*ulCount ulCount*<br/>
Nombre d'éléments.

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’éléments dans l’objet. `CComSafeArrayBound`

## <a name="ccomsafearrayboundsetlowerbound"></a><a name="setlowerbound"></a>CComSafeArrayBound::SetLowerBound

Appelez cette méthode pour définir la limite inférieure.

```
LONG SetLowerBound(LONG lLowerBound) throw();
```

### <a name="parameters"></a>Paramètres

*lLowerBound (en)*<br/>
Limite inférieure.

### <a name="return-value"></a>Valeur de retour

Retourne la nouvelle limite `CComSafeArrayBound` inférieure de l’objet.

### <a name="remarks"></a>Notes

Si le tableau doit être consulté à partir d’un programme Visual CMD, il est recommandé que la limite inférieure soit définie comme 0. Il peut être préférable d’utiliser une valeur limite inférieure différente si le tableau doit être utilisé avec d’autres langues, telles que Visual Basic.

La limite supérieure dépend du nombre d’éléments et de la valeur inférieure. Par exemple, si la limite inférieure est de 0 et que le nombre d’éléments est de 10, la limite supérieure sera automatiquement réglée à 9.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
