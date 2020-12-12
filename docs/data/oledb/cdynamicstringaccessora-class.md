---
description: 'En savoir plus sur : classe CDynamicStringAccessorA'
title: CDynamicStringAccessorA, classe
ms.date: 11/04/2016
f1_keywords:
- CDynamicStringAccessorA
helpviewer_keywords:
- CDynamicStringAccessorA class
ms.assetid: ed0d9821-a655-41f1-a902-43c3042ac49c
ms.openlocfilehash: 45a4d10c8a50c4009151fa90e51172405047a21a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170722"
---
# <a name="cdynamicstringaccessora-class"></a>CDynamicStringAccessorA, classe

Vous permet d’accéder à une source de données lorsque vous n’avez aucune connaissance du schéma de base de données (structure sous-jacente).

## <a name="syntax"></a>Syntaxe

```cpp
typedef CDynamicStringAccessorT<CHAR, DBTYPE_STR> CDynamicStringAccessorA;
```

## <a name="remarks"></a>Notes

Ils demandent tous deux que le fournisseur récupère toutes les données accessibles depuis le magasin de données en tant que données de chaîne, mais `CDynamicStringAccessor` demande les données de chaîne ANSI.

`CDynamicStringAccessorA` hérite `GetString` `SetString` de et de `CDynamicStringAccessor` . Lorsque vous utilisez ces méthodes dans un `CDynamicStringAccessorA` objet, `BaseType` est **char**.

## <a name="requirements"></a>Spécifications

**En-tête**: atldbcli. h

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Informations de référence sur les modèles de consommateurs OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor, classe](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor (classe)](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor, classe](../../data/oledb/cmanualaccessor-class.md)<br/>
[CDynamicAccessor, classe](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessor, classe](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
