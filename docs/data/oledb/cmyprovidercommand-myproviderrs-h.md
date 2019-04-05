---
title: CCustomCommand (CustomRS.H)
ms.date: 10/22/2018
f1_keywords:
- cmyprovidercommand
- myproviderrs.h
- ccustomcommand
- customrs.h
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderCommand class in MyProviderRS.H
- CCustomCommand class in CustomRS.H
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
ms.openlocfilehash: b10d7bccae6fa9b86d072b8e13791f23516b2c63
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028559"
---
# <a name="ccustomcommand-customrsh"></a>CCustomCommand (CustomRS.H)

Le `CCustomCommand` classe est l’implémentation de l’objet de commande fournisseur. Il fournit l’implémentation pour le `IAccessor`, `ICommandText`, et `ICommandProperties` interfaces. Le `IAccessor` interface est identique à celui de l’ensemble de lignes. L’objet de commande utilise l’accesseur pour spécifier les liaisons des paramètres. L’objet rowset les utilise pour spécifier des liaisons pour les colonnes de sortie. Le `ICommandText` interface est un moyen utile pour spécifier une commande textuellement. Cet exemple utilise le `ICommandText` interface ultérieurement quand il ajoute du code personnalisé ; il remplace également le `ICommand::Execute` (méthode). Le `ICommandProperties` interface gère toutes les propriétés pour les objets command et rowset.

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

Le `IAccessor` interface gère toutes les liaisons utilisées dans les commandes et les ensembles de lignes. Le consommateur appelle `IAccessor::CreateAccessor` avec un tableau de `DBBINDING` structures. Chaque `DBBINDING` structure contient des informations sur la manière de gérer les liaisons de colonne (par exemple, le type et la longueur). Le fournisseur reçoit les structures et détermine ensuite la façon dont les données doivent être transférées et si des conversions sont nécessaires. Le `IAccessor` interface est utilisée dans l’objet de commande pour gérer des paramètres de la commande.

L’objet de commande fournit également une implémentation de `IColumnsInfo`. OLE DB requiert le `IColumnsInfo` interface. L’interface permet au consommateur d’extraire des informations sur les paramètres de la commande. L’objet rowset utilise le `IColumnsInfo` interface à retourner des informations sur les colonnes de sortie pour le fournisseur.

Le fournisseur contient également une interface appelée `IObjectWithSite`. Le `IObjectWithSite` interface a été implémentée dans ATL 2.0 et permet à l’implémenteur de passer des informations sur lui-même à son enfant. L’objet de commande utilise le `IObjectWithSite` informations indiquant les généré objets ensemble de lignes qui les a créés.

## <a name="see-also"></a>Voir aussi

[Fichiers générés par l'Assistant Fournisseur](../../data/oledb/provider-wizard-generated-files.md)