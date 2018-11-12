---
title: CAccessorBase, classe
ms.date: 11/04/2016
f1_keywords:
- CAccessorBase
- CAccessorBase.Close
- CAccessorBase::Close
- GetHAccessor
- CAccessorBase::GetHAccessor
- CAccessorBase.GetHAccessor
- CAccessorBase::GetNumAccessors
- GetNumAccessors
- CAccessorBase.GetNumAccessors
- IsAutoAccessor
- CAccessorBase.IsAutoAccessor
- CAccessorBase::IsAutoAccessor
- CAccessorBase::ReleaseAccessors
- CAccessorBase.ReleaseAccessors
- ReleaseAccessors
helpviewer_keywords:
- CAccessorBase class
- Close method
- GetHAccessor method
- GetNumAccessors method
- IsAutoAccessor method
- ReleaseAccessors method
ms.assetid: 389b65be-11ca-4ae0-9290-60c621c4982b
ms.openlocfilehash: 5fb39d2291c2698dc57150eb44a6bbd6778812bb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509304"
---
# <a name="caccessorbase-class"></a>CAccessorBase, classe

Tous les accesseurs dans les modèles OLE DB dérivent de cette classe. `CAccessorBase` permet à un ensemble de lignes gérer plusieurs accesseurs. Il fournit également la liaison pour les paramètres et colonnes de sortie.

## <a name="syntax"></a>Syntaxe

```cpp
// Replace with syntax
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[Fermer](#close)|Ferme les accesseurs.|
|[GetHAccessor](#geth)|Récupère le handle d’accesseur.|
|[GetNumAccessors](#getnum)|Récupère le nombre d’accesseurs créé par la classe.|
|[IsAutoAccessor](#isauto)|Teste si l’accesseur spécifié est un auto-accesseur.|
|[ReleaseAccessors](#release)|Libère les accesseurs.|

## <a name="requirements"></a>Configuration requise

**En-tête :** atldbcli.h

## <a name="close"></a> CAccessorBase::Close

Ferme les accesseurs.

### <a name="syntax"></a>Syntaxe

```cpp
void Close();
```

### <a name="remarks"></a>Notes

Vous devez appeler [ReleaseAccessors](../../data/oledb/caccessorbase-releaseaccessors.md) premier.

## <a name="geth"></a> CAccessorBase::GetHAccessor

Récupère le handle d’accesseur d’un accesseur spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
HACCESSOR GetHAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>Paramètres

*nAccessor*<br/>
[in] Le nombre de décalage de zéro pour l’accesseur.

### <a name="return-value"></a>Valeur de retour

Le handle d’accesseur.

## <a name="getnum"></a> CAccessorBase::GetNumAccessors

Récupère le nombre d’accesseurs créé par la classe.

### <a name="syntax"></a>Syntaxe

```cpp
ULONG GetNumAccessors() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’accesseurs créé par la classe.

## <a name="isauto"></a> CAccessorBase::IsAutoAccessor

Retourne la valeur true si les données sont récupérées automatiquement pour l’accesseur pendant une opération de déplacement.

### <a name="syntax"></a>Syntaxe

```cpp
bool IsAutoAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>Paramètres

*nAccessor*<br/>
[in] Le nombre de décalage de zéro pour l’accesseur.

### <a name="return-value"></a>Valeur de retour

Retourne **true** si l’accesseur est un auto-accesseur. Sinon, elle retourne **False**.

## <a name="release"></a> CAccessorBase::ReleaseAccessors

Libère les accesseurs créés par la classe.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT ReleaseAccessors(IUnknown* pUnk);
```

#### <a name="parameters"></a>Paramètres

*pUnk*<br/>
[in] Un pointeur vers un `IUnknown` interface pour l’objet COM pour lequel les accesseurs ont été créés.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Appelée à partir de [CAccessorRowset::Close](../../data/oledb/caccessorrowset-close.md).

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessorBase, classe](../../data/oledb/caccessorbase-class.md)