---
title: CComSafeArrayBound, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: a79079c95536746cf5a4fa4b35caf39a55ca0f42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62246138"
---
# <a name="ccomsafearraybound-class"></a>CComSafeArrayBound, classe

Cette classe est un wrapper pour un [SAFEARRAYBOUND](/windows/desktop/api/oaidl/ns-oaidl-tagsafearraybound) structure.

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
|[GetLowerBound](#getlowerbound)|Appelez cette méthode pour retourner la limite inférieure.|
|[GetUpperBound](#getupperbound)|Appelez cette méthode pour retourner la limite supérieure.|
|[SetCount](#setcount)|Appelez cette méthode pour définir le nombre d’éléments.|
|[SetLowerBound](#setlowerbound)|Appelez cette méthode pour définir la limite inférieure.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[operator =](#operator_eq)|Définit le `CComSafeArrayBound` à une nouvelle valeur.|

## <a name="remarks"></a>Notes

Cette classe est un wrapper pour le `SAFEARRAYBOUND` structure utilisée par [CComSafeArray](../../atl/reference/ccomsafearray-class.md). Il fournit des méthodes pour interroger et définir les limites supérieures et inférieures d’une dimension unique d’un `CComSafeArray` objet et le nombre d’éléments qu’il contient. Un multidimensionnelles `CComSafeArray` objet utilise un tableau de `CComSafeArrayBound` objets, un pour chaque dimension. Par conséquent, lorsque vous utilisez des méthodes telles que [GetCount](#getcount), n’oubliez pas que cette méthode ne retournera pas le nombre total d’éléments dans un tableau multidimensionnel.

**En-tête :** atlsafe.h

## <a name="requirements"></a>Configuration requise

**En-tête :** atlsafe.h

##  <a name="ccomsafearraybound"></a>  CComSafeArrayBound::CComSafeArrayBound

Constructeur.

```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```

### <a name="parameters"></a>Paramètres

*ulCount*<br/>
Nombre d’éléments dans le tableau.

*lLowerBound*<br/>
La limite inférieure à partir de laquelle le tableau est numéroté.

### <a name="remarks"></a>Notes

Si le tableau est accessible à partir d’un programme Visual C++, il est recommandé que la limite inférieure est définie comme 0. Il peut être préférable d’utiliser une valeur de limite inférieure différente si le tableau doit être utilisé avec d’autres langages, tels que Visual Basic.

##  <a name="getcount"></a>  CComSafeArrayBound::GetCount

Appelez cette méthode pour retourner le nombre d’éléments.

```
ULONG GetCount() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’éléments.

### <a name="remarks"></a>Notes

Si le texte associé `CComSafeArray` objet représente un tableau multidimensionnel, cette méthode retourne uniquement le nombre total d’éléments dans la dimension la plus à droite. Utilisez [CComSafeArray::GetCount](../../atl/reference/ccomsafearray-class.md#getcount) pour obtenir le nombre total d’éléments.

##  <a name="getlowerbound"></a>  CComSafeArrayBound::GetLowerBound

Appelez cette méthode pour retourner la limite inférieure.

```
LONG GetLowerBound() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la limite inférieure de la `CComSafeArrayBound` objet.

##  <a name="getupperbound"></a>  CComSafeArrayBound::GetUpperBound

Appelez cette méthode pour retourner la limite supérieure.

```
LONG GetUpperBound() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la limite supérieure de la `CComSafeArrayBound` objet.

### <a name="remarks"></a>Notes

La limite supérieure varie selon le nombre d’éléments et la valeur de limite inférieure. Par exemple, si la limite inférieure est 0 et le nombre d’éléments est 10, la limite supérieure est automatiquement définie sur 9.

##  <a name="operator_eq"></a>  CComSafeArrayBound::operator =

Définit le `CComSafeArrayBound` à une nouvelle valeur.

```
CComSafeArrayBound& operator= (const CComSafeArrayBound& bound) throw();
CComSafeArrayBound& operator= (ULONG ulCount) throw();
```

### <a name="parameters"></a>Paramètres

*bound*<br/>
Objet `CComSafeArrayBound`.

*ulCount*<br/>
Nombre d'éléments.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le `CComSafeArrayBound` objet.

### <a name="remarks"></a>Notes

Le `CComSafeArrayBound` objet peut être assigné à l’aide d’un existant `CComSafeArrayBound`, ou en fournissant le nombre d’éléments, dans lequel les cas, la limite inférieure est définie sur 0 par défaut.

##  <a name="setcount"></a>  CComSafeArrayBound::SetCount

Appelez cette méthode pour définir le nombre d’éléments.

```
ULONG SetCount(ULONG ulCount) throw();
```

### <a name="parameters"></a>Paramètres

*ulCount*<br/>
Nombre d'éléments.

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’éléments dans le `CComSafeArrayBound` objet.

##  <a name="setlowerbound"></a>  CComSafeArrayBound::SetLowerBound

Appelez cette méthode pour définir la limite inférieure.

```
LONG SetLowerBound(LONG lLowerBound) throw();
```

### <a name="parameters"></a>Paramètres

*lLowerBound*<br/>
La limite inférieure.

### <a name="return-value"></a>Valeur de retour

Retourne la nouvelle limite inférieure de la `CComSafeArrayBound` objet.

### <a name="remarks"></a>Notes

Si le tableau est accessible à partir d’un programme Visual C++, il est recommandé que la limite inférieure est définie comme 0. Il peut être préférable d’utiliser une valeur de limite inférieure différente si le tableau doit être utilisé avec d’autres langages, tels que Visual Basic.

La limite supérieure varie selon le nombre d’éléments et la valeur de limite inférieure. Par exemple, si la limite inférieure est 0 et le nombre d’éléments est 10, la limite supérieure est automatiquement définie sur 9.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
