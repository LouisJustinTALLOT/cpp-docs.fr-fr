---
title: Chaînes de modèles, Assistant Application MFC de document | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.exe.doctemp
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard, document template strings
ms.assetid: 8109f662-3182-4682-977a-2503321c678a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2b1e30ac1e4381cdcd80eddd7fdd4ea27bde5a4
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700568"
---
# <a name="document-template-strings-mfc-application-wizard"></a>Chaînes modèles de document, Assistant Application MFC
Dans cette page de l’Assistant Application MFC, fournir ou d’affiner les options suivantes pour faciliter la gestion des documents et de localisation. Chaînes modèles de document sont disponibles pour les applications qui incluent **support de l’architecture Document/vue** dans le [Type d’Application](../../mfc/reference/application-type-mfc-application-wizard.md). Ils ne sont pas disponibles pour les boîtes de dialogue. Étant donné que la plupart des chaînes de modèles de document sont visibles et employées par les utilisateurs de l’application, elles sont traduites dans le **langue de ressource** indiqué dans le **Type d’Application** page de l’Assistant.  
  
- **Chaînes non localisées**

   S’applique aux applications qui créent des documents utilisateur. Les utilisateurs peuvent ouvrir, imprimer et enregistrer des documents plus facilement si vous fournissez une extension de fichier et un ID de type de fichier. Ces éléments ne sont pas localisés, car ils sont utilisés par le système plutôt que par l’utilisateur.  
  
   |Option|Description|  
   |------------|-----------------|  
   |**Extension de fichier**|Définit l’extension de fichier associée aux documents que l’utilisateur enregistre lors de l’utilisation de l’application. Par exemple, si votre projet est nommé Widget, vous pouvez nommer l’extension de fichier .wgt. (Lorsque vous entrez l’extension de fichier, n’incluez pas la période.)<br /><br /> Si vous fournissez une extension de fichier, l’Explorateur peut imprimer des documents de votre application sans lancer votre application lorsque l’utilisateur dépose l’icône de document sur l’icône de l’imprimante.<br /><br /> Si vous ne spécifiez pas une extension, un utilisateur doit spécifier une extension de fichier lors de l’enregistrement de fichiers. L’Assistant ne fournit pas une extension de fichier par défaut.|  
   |**ID de type de fichier**|Définit l’étiquette pour votre type de document dans le Registre système.|  
  
- **Chaînes localisées**

   Génère des chaînes associées à l’application et le document qui sont lus et utilisé par les utilisateurs de l’application, et donc les chaînes sont localisées.  
  
   |Option|Description|  
   |------------|-----------------|  
   |**Language**|Indique la langue dans laquelle les chaînes sont affichées pour toutes les zones sous **des chaînes localisées**. Pour modifier la valeur de cette zone, sélectionnez la langue appropriée sous **langue de ressource** dans le [Type d’Application](../../mfc/reference/application-type-mfc-application-wizard.md) page de l’Assistant Application MFC.|  
   |**Titre du frame principal**|Définit le texte qui apparaît en haut du frame principal de l’application. Par défaut, le nom du projet.|  
   |**Nom de type de document**|Identifie le type de document sous lequel un document de l’application peut être regroupé. Par défaut, le nom du projet. Modification de la valeur par défaut ne modifie pas les options dans cette boîte de dialogue.|  
   |**Nom du filtre**|Définit le nom de que vos utilisateurs peuvent indiquer pour rechercher les fichiers de votre type de fichier. Cette option est disponible à partir de la **types de fichiers** et **enregistrer en tant que type** options dans le Windows standard **Open** et **enregistrer en tant que** boîtes de dialogue. Par défaut, le nom du projet et les fichiers, suivi de l’extension fournie dans **extension de fichier**. Par exemple, si votre projet est nommé Widget, et l’extension de fichier est .wgt, le **nom de filtre** est Widget Files (*.wgt) par défaut.|  
   |**Nom court de nouveau fichier**|Définit le nom apparaissant dans le Windows standard **New** boîte de dialogue, s’il existe plus d’un nouveau modèle de document. Si votre application est un [serveur Automation](../../mfc/automation-servers.md), ce nom est utilisé en tant que le nom court de votre objet Automation. Par défaut, le nom du projet.|  
   |**Nom de type de fichier long**|Définit le nom de type de fichier dans le Registre système. Si votre application est un serveur Automation, ce nom est utilisé en tant que le nom long de votre objet Automation. Par défaut, le nom de projet plus (+). Document.|  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md)

