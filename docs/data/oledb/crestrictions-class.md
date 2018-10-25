---
title: CRestrictions, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CRestrictions
- CRestrictions
- ATL.CRestrictions
- CRestrictions.Open
- ATL::CRestrictions::Open
- ATL.CRestrictions.Open
- CRestrictions::Open
dev_langs:
- C++
helpviewer_keywords:
- CRestrictions class
- Open method
ms.assetid: 0aaa2364-641c-4318-b110-7446aada4b4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a4ea0536a8af87927521f88d888e19aa145f2c04
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50072068"
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

## <a name="requirements"></a>Configuration requise

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

Consultez [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686) pour plus d’informations sur les restrictions définies sur chaque ensemble de lignes de schéma.

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Classes de jeu de lignes du schéma et classes Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)