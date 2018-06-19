---
title: CMyProviderCommand (MyProviderRS.H) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyprovidercommand
- myproviderrs.h
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderCommand class in MyProviderRS.H
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8c18742d9b3b1039033ad8d42939e0f5a4578fbb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098145"
---
# <a name="cmyprovidercommand-myproviderrsh"></a>CMyProviderCommand (MyProviderRS.H)
La `CMyProviderCommand` classe est l’implémentation de l’objet de commande fournisseur. Il fournit l’implémentation pour la `IAccessor`, `ICommandText`, et **ICommandProperties** interfaces. Le `IAccessor` interface est le même que celui de l’ensemble de lignes. L’objet de commande utilise l’accesseur pour spécifier les liaisons de paramètres. L’objet rowset les utilise pour spécifier les liaisons pour les colonnes de sortie. Le `ICommandText` interface est un moyen utile pour spécifier une commande textuelle. Cet exemple utilise le `ICommandText` interface ultérieurement lors de l’ajout de code personnalisé ; il remplace également le `ICommand::Execute` (méthode). Le **ICommandProperties** interface gère toutes les propriétés pour les objets command et rowset.  
  
```  
// CMyProviderCommand  
class ATL_NO_VTABLE CMyProviderCommand :   
class ATL_NO_VTABLE CMyProviderCommand :   
   public CComObjectRootEx<CComSingleThreadModel>,  
   public IAccessorImpl<CMyProviderCommand>,  
   public ICommandTextImpl<CMyProviderCommand>,  
   public ICommandPropertiesImpl<CMyProviderCommand>,  
   public IObjectWithSiteImpl<CMyProviderCommand>,  
   public IConvertTypeImpl<CMyProviderCommand>,  
   public IColumnsInfoImpl<CMyProviderCommand>  
```  
  
 Le `IAccessor` interface gère toutes les liaisons utilisées dans les commandes et les ensembles de lignes. Le consommateur appelle **IAccessor::CreateAccessor** avec un tableau de **DBBINDING** structures. Chaque **DBBINDING** structure contient des informations sur comment les liaisons de colonnes doivent être gérés (par exemple, le type et la longueur). Le fournisseur reçoit les structures, puis détermine comment les données doivent être transférées et si des conversions sont nécessaires. Le `IAccessor` interface est utilisée dans l’objet de commande pour gérer les paramètres de la commande.  
  
 L’objet de commande fournit également une implémentation de `IColumnsInfo`. OLE DB requiert le `IColumnsInfo` interface. L’interface permet au consommateur de récupérer les informations sur les paramètres de la commande. L’objet rowset utilise le `IColumnsInfo` interface à retourner des informations sur les colonnes de sortie pour le fournisseur.  
  
 Le fournisseur contient également une interface appelée `IObjectWithSite`. Le `IObjectWithSite` interface a été implémentée dans ATL 2.0 et permet à l’implémenteur de passer des informations sur lui-même à son enfant. L’objet de commande utilise le `IObjectWithSite` pour indiquer les informations générées objets ensemble de lignes qui les a créés.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers générés par l’Assistant Fournisseur](../../data/oledb/provider-wizard-generated-files.md)