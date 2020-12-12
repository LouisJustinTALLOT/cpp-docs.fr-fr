---
description: 'En savoir plus sur : CCustomCommand (Customers. H)'
title: CCustomCommand (CustomRS.H)
ms.date: 10/22/2018
f1_keywords:
- cmyprovidercommand
- ccustomcommand
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderCommand class in MyProviderRS.H
- CCustomCommand class in CustomRS.H
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
ms.openlocfilehash: 35b0e1a1628920a85343a52ce4a003302468884b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170501"
---
# <a name="ccustomcommand-customrsh"></a>CCustomCommand (CustomRS.H)

La `CCustomCommand` classe est l’implémentation de l’objet de commande du fournisseur. Il fournit l’implémentation pour les `IAccessor` `ICommandText` interfaces, et `ICommandProperties` . L' `IAccessor` interface est identique à celle de l’ensemble de lignes. L’objet Command utilise l’accesseur pour spécifier des liaisons pour les paramètres. L’objet rowset les utilise pour spécifier des liaisons pour les colonnes de sortie. L' `ICommandText` interface est un moyen utile de spécifier une commande textuellement. Cet exemple utilise l' `ICommandText` interface ultérieurement lorsqu’il ajoute du code personnalisé ; il substitue également la `ICommand::Execute` méthode. L' `ICommandProperties` interface gère toutes les propriétés des objets Command et rowset.

```cpp
// CCustomCommand
class ATL_NO_VTABLE CCustomCommand :
class ATL_NO_VTABLE CCustomCommand :
   public CComObjectRootEx<CComSingleThreadModel>,
   public IAccessorImpl<CCustomCommand>,
   public ICommandTextImpl<CCustomCommand>,
   public ICommandPropertiesImpl<CCustomCommand>,
   public IObjectWithSiteImpl<CCustomCommand>,
   public IConvertTypeImpl<CCustomCommand>,
   public IColumnsInfoImpl<CCustomCommand>
```

L' `IAccessor` interface gère toutes les liaisons utilisées dans les commandes et les ensembles de lignes. Le consommateur appelle `IAccessor::CreateAccessor` avec un tableau de `DBBINDING` structures. Chaque `DBBINDING` structure contient des informations sur la façon dont les liaisons de colonne doivent être gérées (telles que le type et la longueur). Le fournisseur reçoit les structures, puis détermine la façon dont les données doivent être transférées, ainsi que les conversions nécessaires. L' `IAccessor` interface est utilisée dans l’objet Command pour gérer les paramètres de la commande.

L’objet Command fournit également une implémentation de `IColumnsInfo` . OLE DB requiert l' `IColumnsInfo` interface. L’interface permet au consommateur de récupérer des informations sur les paramètres à partir de la commande. L’objet rowset utilise l' `IColumnsInfo` interface pour retourner les informations sur les colonnes de sortie au fournisseur.

Le fournisseur contient également une interface appelée `IObjectWithSite` . L' `IObjectWithSite` interface a été implémentée dans ATL 2,0 et permet à l’implémenteur de passer des informations sur lui-même à son enfant. L’objet Command utilise les `IObjectWithSite` informations pour indiquer à tous les objets rowset générés à propos de qui les a créés.

## <a name="see-also"></a>Voir aussi

[Fichiers de Wizard-Generated du fournisseur](../../data/oledb/provider-wizard-generated-files.md)
