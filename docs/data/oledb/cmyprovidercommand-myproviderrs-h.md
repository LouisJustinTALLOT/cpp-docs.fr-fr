---
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
ms.openlocfilehash: afa8571173117a23962eb84f6fa5b4cf2c3c46e7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211755"
---
# <a name="ccustomcommand-customrsh"></a>CCustomCommand (CustomRS.H)

La classe `CCustomCommand` est l’implémentation de l’objet de commande du fournisseur. Il fournit l’implémentation pour les interfaces `IAccessor`, `ICommandText`et `ICommandProperties`. L’interface `IAccessor` est identique à celle de l’ensemble de lignes. L’objet Command utilise l’accesseur pour spécifier des liaisons pour les paramètres. L’objet rowset les utilise pour spécifier des liaisons pour les colonnes de sortie. L’interface `ICommandText` est un moyen utile de spécifier une commande textuellement. Cet exemple utilise l’interface `ICommandText` ultérieurement lorsqu’il ajoute du code personnalisé. elle remplace également la méthode `ICommand::Execute`. L’interface `ICommandProperties` gère toutes les propriétés des objets Command et rowset.

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

L’interface `IAccessor` gère toutes les liaisons utilisées dans les commandes et les ensembles de lignes. Le consommateur appelle `IAccessor::CreateAccessor` avec un tableau de structures `DBBINDING`. Chaque structure `DBBINDING` contient des informations sur la façon dont les liaisons de colonne doivent être gérées (telles que le type et la longueur). Le fournisseur reçoit les structures, puis détermine la façon dont les données doivent être transférées, ainsi que les conversions nécessaires. L’interface `IAccessor` est utilisée dans l’objet Command pour gérer les paramètres de la commande.

L’objet Command fournit également une implémentation de `IColumnsInfo`. OLE DB requiert l’interface `IColumnsInfo`. L’interface permet au consommateur de récupérer des informations sur les paramètres à partir de la commande. L’objet rowset utilise l’interface `IColumnsInfo` pour retourner les informations sur les colonnes de sortie au fournisseur.

Le fournisseur contient également une interface appelée `IObjectWithSite`. L’interface `IObjectWithSite` a été implémentée dans ATL 2,0 et permet à l’implémenteur de passer des informations sur lui-même à son enfant. L’objet Command utilise les informations de `IObjectWithSite` pour indiquer à tous les objets rowset générés à propos de qui les a créés.

## <a name="see-also"></a>Voir aussi

[Fichiers générés par l’Assistant Fournisseur](../../data/oledb/provider-wizard-generated-files.md)
