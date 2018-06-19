---
title: Chaînes de modèles, Assistant Application MFC de document | Documents Microsoft
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
ms.openlocfilehash: 7d6039459eed097af5e927c4bd2f30d3e7c3c4bc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373538"
---
# <a name="document-template-strings-mfc-application-wizard"></a>Chaînes modèles de document, Assistant Application MFC
Dans cette page de l’Assistant Application MFC, fournir ou d’affiner les options suivantes pour faciliter la localisation et gestion des documents. Chaînes modèles de document sont disponibles pour les applications qui incluent **prise en charge d’architecture Document/vue** dans les [Type d’Application](../../mfc/reference/application-type-mfc-application-wizard.md). Ils ne sont pas disponibles pour les boîtes de dialogue. Étant donné que la plupart des chaînes modèles de document sont visibles et employées par les utilisateurs de l’application, elles sont traduites dans la **langue de ressource** indiqué dans le **Type d’Application** page de l’Assistant.  
  
 **Chaînes non localisés**  
 S’applique aux applications qui créent des documents utilisateur. Les utilisateurs peuvent ouvrir, imprimer et enregistrer des documents plus facilement si vous fournissez une extension de fichier et un ID de type de fichier. Ces éléments ne sont pas localisés, car ils sont utilisés par le système plutôt que par l’utilisateur.  
  
|Option|Description|  
|------------|-----------------|  
|**Extension de fichier**|Définit l’extension de fichier associée aux documents que l’utilisateur enregistre lors de l’utilisation de l’application. Par exemple, si votre projet est nommé Widget, vous pouvez nommer l’extension de fichier .wgt. (Lorsque vous entrez l’extension de fichier, n’incluez pas la période.)<br /><br /> Si vous fournissez une extension de fichier, l’Explorateur peut imprimer des documents de votre application sans lancer votre application lorsque l’utilisateur dépose l’icône de document sur l’icône imprimante.<br /><br /> Si vous ne spécifiez pas une extension, un utilisateur doit spécifier une extension de fichier lors de l’enregistrement de fichiers. L’Assistant ne fournit pas une extension de fichier par défaut.|  
|**ID du type de fichier**|Définit l’étiquette pour votre type de document dans le Registre système.|  
  
 **Chaînes localisées**  
 Génère des chaînes associées à l’application et au document qui sont lues et utilisées par les utilisateurs de l’application, les chaînes sont localisés.  
  
|Option|Description|  
|------------|-----------------|  
|**Language**|Indique la langue dans laquelle les chaînes sont affichées pour toutes les cases sous **des chaînes localisées**. Pour modifier la valeur de cette zone, sélectionnez la langue appropriée sous **langue de ressource** dans les [Type d’Application](../../mfc/reference/application-type-mfc-application-wizard.md) page de l’Assistant Application MFC.|  
|**Titre du frame principal**|Définit le texte qui apparaît en haut du frame de l’application principale. Par défaut, le nom du projet.|  
|**Nom de type de document**|Identifie le type de document sous lequel un document de l’application peut être regroupé. Par défaut, le nom du projet. Modification de la valeur par défaut ne change pas toutes les autres options dans cette boîte de dialogue.|  
|**Nom de filtre**|Définit le nom de que vos utilisateurs peuvent indiquer pour rechercher les fichiers de votre type de fichier. Cette option est disponible à partir de la **types de fichiers** et **enregistrer en tant que type** options dans les fenêtres standards **ouvrir** et **enregistrer en tant que** boîtes de dialogue. Par défaut, le nom du projet plus Files, suivi de l’extension fournie dans **extension de fichier**. Par exemple, si votre projet se nomme Widget et que l’extension de fichier est .wgt, le **nom de filtre** par défaut est Widget Files (*.wgt).|  
|**Nom court de nouveau fichier**|Définit le nom apparaissant dans les fenêtres standards `New` boîte de dialogue, s’il existe plus d’un nouveau modèle de document. Si votre application est un [serveur Automation](../../mfc/automation-servers.md), ce nom est utilisé en tant que le nom court de votre objet Automation. Par défaut, le nom du projet.|  
|**Nom de type de fichier long**|Définit le nom de type de fichier dans le Registre système. Si votre application est un serveur Automation, ce nom est utilisé en tant que le nom long de votre objet Automation. Par défaut, le nom du projet plu. Document.|  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md)

