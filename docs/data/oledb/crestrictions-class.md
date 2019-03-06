---
title: CRestrictions, classe
ms.date: 11/04/2016
f1_keywords:
- ATL::CRestrictions
- CRestrictions
- ATL.CRestrictions
- CRestrictions.Open
- ATL::CRestrictions::Open
- ATL.CRestrictions.Open
- CRestrictions::Open
helpviewer_keywords:
- CRestrictions class
- Open method
ms.assetid: 0aaa2364-641c-4318-b110-7446aada4b4f
ms.openlocfilehash: 3ade541e5418799f525a08d3fc868f07d2bdfe6a
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412820"
---
# <a name="crestrictions-class"></a>CRestrictions, classe

Une classe générique qui vous permet de spécifier des restrictions pour les ensembles de lignes de schéma.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, short nRestrictions, const GUID* pguid>
class CRestrictions :
   public CSchemaRowset <T, nRestrictions>
```

### <a name="parameters"></a>Paramètres

*T*<br/>
La classe utilisée pour l’accesseur.

*nRestrictions*<br/>
Le nombre de colonnes de restriction pour l’ensemble de lignes de schéma.

*pguid*<br/>
Un pointeur vers le GUID pour le schéma.

## <a name="requirements"></a>Spécifications

**En-tête :** atldbsch.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[Ouvrir](#open)|Retourne un résultat défini selon les restrictions fournies par l’utilisateur.|

## <a name="open"></a> CRestrictions::Open

Retourne un résultat défini selon les restrictions fournies par l’utilisateur.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Open(const CSession& session,
   LPCTSTR lpszParam 1 = NULL,
   LPCTSTR lpszParam 2 = NULL,
   LPCTSTR lpszParam 3 = NULL,
   LPCTSTR lpszParam 4 = NULL,
   LPCTSTR lpszParam 5 = NULL,
   LPCTSTR lpszParam 6 = NULL,
   LPCTSTR lpszParam 7 = NULL,
   bool bBind = true);
```

#### <a name="parameters"></a>Paramètres

*session*<br/>
[in] Spécifie un objet de session existant utilisé pour se connecter à la source de données.

*lpszParam*<br/>
[in] Spécifie les restrictions sur l’ensemble de lignes de schéma.

*bBind*<br/>
[in] Spécifie s’il faut lier automatiquement de mapper les colonnes. La valeur par défaut est **true**, ce qui provoque le mappage de colonne à lier automatiquement. Paramètre *bBind* à **false** empêche la liaison automatique de la carte de colonne afin que vous pouvez lier manuellement. (Liaison manuelle est un intérêt particulier pour les utilisateurs OLAP).

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="remarks"></a>Notes

Vous pouvez spécifier un maximum de sept restrictions sur un ensemble de lignes de schéma.

Consultez [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) pour plus d’informations sur les restrictions définies sur chaque ensemble de lignes de schéma.

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Classes de jeu de lignes du schéma et classes Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)