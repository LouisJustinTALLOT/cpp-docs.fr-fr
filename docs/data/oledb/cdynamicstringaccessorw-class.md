---
title: CDynamicStringAccessorW, classe
ms.date: 11/04/2016
f1_keywords:
- CDynamicStringAccessorW
helpviewer_keywords:
- CDynamicStringAccessorW class
ms.assetid: 9b7fd5cc-3a9b-4b57-b907-f1e35de2c98f
ms.openlocfilehash: 7052a912363d1256294131da9b89df97f768ecf8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551357"
---
# <a name="cdynamicstringaccessorw-class"></a>CDynamicStringAccessorW, classe

Vous permet d’accéder à une source de données lorsque vous n’avez aucune connaissance du schéma de base de données (structure sous-jacente).

## <a name="syntax"></a>Syntaxe

```cpp
typedef CDynamicStringAccessorT<WCHAR, DBTYPE_WSTR> CDynamicStringAccessorW;
```

## <a name="remarks"></a>Notes

Les deux demandent que le fournisseur récupère toutes les données accessibles à partir du magasin de données en tant que données de chaîne, mais `CDynamicStringAccessor` demande des données de chaîne Unicode.

`CDynamicStringAccessorW` hérite `GetString` et `SetString` de `CDynamicStringAccessor`. Lorsque vous utilisez ces méthodes dans un `CDynamicStringAccessorW` objet, `BaseType` est **WCHAR**.

## <a name="requirements"></a>Configuration requise

**En-tête**: atldbcli.h

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor, classe](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor, classe](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor, classe](../../data/oledb/cmanualaccessor-class.md)<br/>
[CDynamicAccessor, classe](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessor, classe](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
