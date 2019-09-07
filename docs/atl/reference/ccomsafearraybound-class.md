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
ms.openlocfilehash: 0386092ac26e71fcf5e840594a6b07f56cc9badd
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739746"
---
# <a name="ccomsafearraybound-class"></a>CComSafeArrayBound, classe

Cette classe est un wrapper pour une structure [SAFEARRAYBOUND](/windows/win32/api/oaidl/ns-oaidl-safearraybound) .

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
|[operator =](#operator_eq)|Affecte une nouvelle valeur à.`CComSafeArrayBound`|

## <a name="remarks"></a>Notes

Cette classe est un wrapper pour la `SAFEARRAYBOUND` structure utilisée par [CComSafeArray](../../atl/reference/ccomsafearray-class.md). Il fournit des méthodes pour interroger et définir les limites supérieure et inférieure d’une dimension unique d’un `CComSafeArray` objet et le nombre d’éléments qu’elle contient. Un `CComSafeArray` objet multidimensionnel utilise un tableau d' `CComSafeArrayBound` objets, un pour chaque dimension. Par conséquent, lorsque vous utilisez des méthodes telles que [GetCount](#getcount), sachez que cette méthode ne retourne pas le nombre total d’éléments dans un tableau multidimensionnel.

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
Limite inférieure de laquelle le tableau est numéroté.

### <a name="remarks"></a>Notes

Si le tableau doit être accessible à partir d' C++ un programme, il est recommandé de définir la limite inférieure sur 0. Il peut être préférable d’utiliser une autre valeur de limite inférieure si le tableau doit être utilisé avec d’autres langages, tels que Visual Basic.

##  <a name="getcount"></a>  CComSafeArrayBound::GetCount

Appelez cette méthode pour retourner le nombre d’éléments.

```
ULONG GetCount() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’éléments.

### <a name="remarks"></a>Notes

Si l’objet `CComSafeArray` associé représente un tableau multidimensionnel, cette méthode retourne uniquement le nombre total d’éléments dans la dimension la plus à droite. Utilisez [CComSafeArray :: GetCount](../../atl/reference/ccomsafearray-class.md#getcount) pour obtenir le nombre total d’éléments.

##  <a name="getlowerbound"></a>  CComSafeArrayBound::GetLowerBound

Appelez cette méthode pour retourner la limite inférieure.

```
LONG GetLowerBound() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la limite inférieure de l' `CComSafeArrayBound` objet.

##  <a name="getupperbound"></a>  CComSafeArrayBound::GetUpperBound

Appelez cette méthode pour retourner la limite supérieure.

```
LONG GetUpperBound() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la limite supérieure de l' `CComSafeArrayBound` objet.

### <a name="remarks"></a>Notes

La limite supérieure dépend du nombre d’éléments et de la valeur limite inférieure. Par exemple, si la limite inférieure est 0 et que le nombre d’éléments est 10, la limite supérieure sera automatiquement définie sur 9.

##  <a name="operator_eq"></a>  CComSafeArrayBound::operator =

Affecte une nouvelle valeur à.`CComSafeArrayBound`

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

Retourne un pointeur vers l' `CComSafeArrayBound` objet.

### <a name="remarks"></a>Notes

L' `CComSafeArrayBound` objet peut être assigné à l’aide `CComSafeArrayBound`d’un existant ou en fournissant le nombre d’éléments, auquel cas la limite inférieure est définie sur 0 par défaut.

##  <a name="setcount"></a>  CComSafeArrayBound::SetCount

Appelez cette méthode pour définir le nombre d’éléments.

```
ULONG SetCount(ULONG ulCount) throw();
```

### <a name="parameters"></a>Paramètres

*ulCount*<br/>
Nombre d'éléments.

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’éléments dans l' `CComSafeArrayBound` objet.

##  <a name="setlowerbound"></a>  CComSafeArrayBound::SetLowerBound

Appelez cette méthode pour définir la limite inférieure.

```
LONG SetLowerBound(LONG lLowerBound) throw();
```

### <a name="parameters"></a>Paramètres

*lLowerBound*<br/>
Limite inférieure.

### <a name="return-value"></a>Valeur de retour

Retourne la nouvelle limite inférieure de l' `CComSafeArrayBound` objet.

### <a name="remarks"></a>Notes

Si le tableau doit être accessible à partir d’un C++ programme visuel, il est recommandé de définir la limite inférieure sur 0. Il peut être préférable d’utiliser une autre valeur de limite inférieure si le tableau doit être utilisé avec d’autres langages, tels que Visual Basic.

La limite supérieure dépend du nombre d’éléments et de la valeur limite inférieure. Par exemple, si la limite inférieure est 0 et que le nombre d’éléments est 10, la limite supérieure sera automatiquement définie sur 9.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
