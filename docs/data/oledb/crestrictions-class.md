---
description: 'En savoir plus sur : CRestrictions, classe'
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
ms.openlocfilehash: 28eee2ea8d7e3b28edaab745c48426c878cc2f2d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170280"
---
# <a name="crestrictions-class"></a>CRestrictions, classe

Classe générique qui vous permet de spécifier des restrictions pour les ensembles de lignes de schéma.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, short nRestrictions, const GUID* pguid>
class CRestrictions :
   public CSchemaRowset <T, nRestrictions>
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Classe utilisée pour l’accesseur.

*nRestrictions*<br/>
Nombre de colonnes de restriction pour l’ensemble de lignes de schéma.

*pguid*<br/>
Pointeur vers le GUID du schéma.

## <a name="requirements"></a>Spécifications

**En-tête :** atldbsch. h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

| Nom | Description |
|-|-|
|[Ouvrir](#open)|Retourne un jeu de résultats en fonction des restrictions fournies par l’utilisateur.|

## <a name="crestrictionsopen"></a><a name="open"></a> CRestrictions :: Open

Retourne un jeu de résultats en fonction des restrictions fournies par l’utilisateur.

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
dans Spécifie un objet de session existant utilisé pour se connecter à la source de données.

*lpszParam*<br/>
dans Spécifie les restrictions sur l’ensemble de lignes de schéma.

*bBind*<br/>
dans Spécifie s’il faut lier automatiquement le mappage de colonnes. La valeur par défaut est **`true`** , ce qui entraîne la liaison automatique du mappage de colonnes. La définition de *bBind* **`false`** empêche la liaison automatique de la carte de colonnes afin que vous puissiez la lier manuellement. (La liaison manuelle présente un intérêt particulier pour les utilisateurs OLAP.)

### <a name="return-value"></a>Valeur renvoyée

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Vous pouvez spécifier un maximum de sept restrictions sur un ensemble de lignes de schéma.

Pour plus d’informations sur les restrictions définies sur chaque ensemble de lignes de schéma, consultez [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) .

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Informations de référence sur les modèles de consommateurs OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Classes d’ensemble de lignes de schéma et classes typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)
