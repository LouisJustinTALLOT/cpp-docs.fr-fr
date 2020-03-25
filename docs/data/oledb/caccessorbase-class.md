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
ms.openlocfilehash: 8aef8a04d7adff903e21491a91014d55aab769da
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212290"
---
# <a name="caccessorbase-class"></a>CAccessorBase, classe

Tous les accesseurs des modèles OLE DB dérivent de cette classe. `CAccessorBase` permet à un ensemble de lignes de gérer plusieurs accesseurs. Il fournit également une liaison pour les paramètres et les colonnes de sortie.

## <a name="syntax"></a>Syntaxe

```cpp
// Replace with syntax
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[Close](#close)|Ferme les accesseurs.|
|[GetHAccessor](#geth)|Récupère le handle d’accesseur.|
|[GetNumAccessors](#getnum)|Récupère le nombre d’accesseurs créés par la classe.|
|[IsAutoAccessor](#isauto)|Teste si l’accesseur spécifié est un autoaccesseur.|
|[ReleaseAccessors](#release)|Libère les accesseurs.|

## <a name="requirements"></a>Spécifications

**En-tête :** atldbcli.h

## <a name="caccessorbaseclose"></a><a name="close"></a>CAccessorBase :: Close

Ferme les accesseurs.

### <a name="syntax"></a>Syntaxe

```cpp
void Close();
```

### <a name="remarks"></a>Notes

Vous devez d’abord appeler [ReleaseAccessors](../../data/oledb/caccessorbase-releaseaccessors.md) .

## <a name="caccessorbasegethaccessor"></a><a name="geth"></a>CAccessorBase :: GetHAccessor

Récupère le handle d’accesseur d’un accesseur spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
HACCESSOR GetHAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>Paramètres

*nAccessor*<br/>
dans Nombre de décalage zéro pour l’accesseur.

### <a name="return-value"></a>Valeur de retour

Handle d’accesseur.

## <a name="caccessorbasegetnumaccessors"></a><a name="getnum"></a>CAccessorBase :: GetNumAccessors

Récupère le nombre d’accesseurs créés par la classe.

### <a name="syntax"></a>Syntaxe

```cpp
ULONG GetNumAccessors() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’accesseurs créés par la classe.

## <a name="caccessorbaseisautoaccessor"></a><a name="isauto"></a>CAccessorBase :: IsAutoAccessor

Retourne la valeur true si les données sont récupérées automatiquement pour l’accesseur pendant une opération de déplacement.

### <a name="syntax"></a>Syntaxe

```cpp
bool IsAutoAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>Paramètres

*nAccessor*<br/>
dans Nombre de décalage zéro pour l’accesseur.

### <a name="return-value"></a>Valeur de retour

Retourne la **valeur true** si l’accesseur est un autoaccesseur. Sinon, elle retourne **False**.

## <a name="caccessorbasereleaseaccessors"></a><a name="release"></a>CAccessorBase :: ReleaseAccessors

Libère les accesseurs créés par la classe.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT ReleaseAccessors(IUnknown* pUnk);
```

#### <a name="parameters"></a>Paramètres

*pUnk*<br/>
dans Pointeur vers une interface `IUnknown` pour l’objet COM pour lequel les accesseurs ont été créés.

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

### <a name="remarks"></a>Notes

Appelé à partir de [CAccessorRowset :: Close](../../data/oledb/caccessorrowset-close.md).

## <a name="see-also"></a>Voir aussi

[OLE DB (modèles du consommateur)](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessorBase, classe](../../data/oledb/caccessorbase-class.md)
