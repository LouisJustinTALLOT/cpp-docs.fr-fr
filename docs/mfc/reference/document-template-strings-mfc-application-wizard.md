---
description: 'En savoir plus sur : chaînes de modèles de document, Assistant Application MFC'
title: Chaînes modèles de document, Assistant Application MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.doctemp
helpviewer_keywords:
- MFC Application Wizard, document template strings
ms.assetid: 8109f662-3182-4682-977a-2503321c678a
ms.openlocfilehash: 839626915b5e60dd47182dd42f1182a092f0b3ce
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219913"
---
# <a name="document-template-strings-mfc-application-wizard"></a>Chaînes modèles de document, Assistant Application MFC

Dans cette page de l’Assistant Application MFC, fournissez ou Affinez les options suivantes pour faciliter la gestion et la localisation des documents. Les chaînes de modèle de document sont disponibles pour les applications qui incluent la **prise en charge de l’architecture document/vue** dans le [type d’application](../../mfc/reference/application-type-mfc-application-wizard.md). Elles ne sont pas disponibles pour les boîtes de dialogue. Étant donné que la plupart des chaînes de modèle de document sont visibles et utilisées par les utilisateurs de l’application, elles sont localisées dans la **langue de ressource** indiquée dans la page **type d’application** de l’Assistant.

- **Chaînes non localisées**

   S’applique aux applications qui créent des documents utilisateur. Les utilisateurs peuvent ouvrir, imprimer et enregistrer des documents plus facilement si vous fournissez une extension de fichier et un ID de type de fichier. Ces éléments ne sont pas localisés, car ils sont utilisés par le système plutôt que par l’utilisateur.

   |Option|Description|
   |------------|-----------------|
   |**Extension de fichier**|Définit l’extension de fichier associée aux documents enregistrés par l’utilisateur lors de l’utilisation de l’application. Par exemple, si votre projet est nommé widget, vous pouvez nommer l’extension de fichier. WGT. (Lorsque vous entrez l’extension de fichier, n’incluez pas le point.)<br /><br /> Si vous fournissez une extension de fichier, l’Explorateur peut imprimer les documents de votre application sans lancer votre application lorsque l’utilisateur dépose l’icône de document sur une icône d’imprimante.<br /><br /> Si vous ne spécifiez pas d’extension, un utilisateur doit spécifier une extension de fichier lors de l’enregistrement des fichiers. L’Assistant ne fournit pas d’extension de fichier par défaut.|
   |**ID de type de fichier**|Définit l’étiquette de votre type de document dans le registre système.|

- **Chaînes localisées**

   Produit des chaînes associées à l’application et au document qui sont lues et utilisées par les utilisateurs de l’application, de sorte que les chaînes sont localisées.

   |Option|Description|
   |------------|-----------------|
   |**Langage**|Indique la langue dans laquelle les chaînes sont affichées pour toutes les zones sous les **chaînes localisées**. Pour modifier la valeur dans cette zone, sélectionnez la langue appropriée sous **langue des ressources** dans la page [type d’application](../../mfc/reference/application-type-mfc-application-wizard.md) de l’Assistant Application MFC.|
   |**Légende du frame principal**|Définit le texte qui apparaît en haut du frame principal de l’application. Par défaut, le nom du projet.|
   |**Nom du type de document**|Identifie le type de document sous lequel un document de l’application peut être regroupé. Par défaut, le nom du projet. La modification de la valeur par défaut ne modifie pas les autres options de cette boîte de dialogue.|
   |**Nom du filtre**|Définit le nom que vos utilisateurs peuvent indiquer pour rechercher les fichiers de votre type de fichier. Cette option est disponible à partir des options **fichiers de type** et **Enregistrer sous** dans les boîtes de dialogue Windows standard **ouvrir** et **Enregistrer sous** . Par défaut, le nom du projet plus fichiers, suivi de l’extension fournie dans **extension de fichier**. Par exemple, si votre projet est nommé widget et que l’extension de fichier est. WGT, le **nom de filtre** est widget Files (*. WGT) par défaut.|
   |**Nom du nouveau fichier**|Définit le nom qui apparaît dans la boîte de dialogue **nouveau** Windows standard, s’il existe plusieurs nouveaux modèles de document. Si votre application est un [serveur Automation](../../mfc/automation-servers.md), ce nom est utilisé comme nom abrégé de votre objet Automation. Par défaut, le nom du projet.|
   |**Nom long du type de fichier**|Définit le nom du type de fichier dans le registre système. Si votre application est un serveur Automation, ce nom est utilisé comme nom long de votre objet Automation. Par défaut, le nom du projet est plus. Document.|

## <a name="see-also"></a>Voir aussi

[Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md)
