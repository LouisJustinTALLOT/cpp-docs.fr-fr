---
title: Prise en charge des documents composés, Assistant Application MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.compdoc
ms.assetid: 42e1af83-12c4-438d-92eb-13835afdb148
ms.openlocfilehash: 572bb10d8aa2af38858bac50f795fb660d5476b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543037"
---
# <a name="compound-document-support-mfc-application-wizard"></a>Prise en charge des documents composés, Assistant Application MFC

Dans cette page de l’Assistant Application MFC, indiquer à quel niveau de votre application fournit une prise en charge des documents composés et actifs. Votre application doit prendre en charge l’architecture document/vue pour prendre en charge des documents composés et les modèles de document.

Par défaut, l’application ne contient aucune prise en charge de document composé. Si vous acceptez cette valeur par défaut, votre application ne peut pas prendre en charge les documents actifs ou les fichiers composés.

- **Prise en charge des documents composés**

   Détermine si votre application fournit la prise en charge du conteneur, prise en charge du serveur ou les deux. Pour plus d’informations sur cette zone, consultez :

   - [Conteneurs : implémentation d’un conteneur](../../mfc/containers-implementing-a-container.md)

   - [Serveurs : implémentation d’un serveur](../../mfc/servers-implementing-a-server.md)

   |Option|Description|
   |------------|-----------------|
   |**Aucun**|N’indique aucune prise en charge pour Object Linking and Embedding (OLE). Par défaut, l’Assistant application crée une application sans prise en charge ActiveX.|
   |**Conteneur**|Contient des objets liés et incorporés.|
   |**Mini-serveur**|Indique l’application peut créer et gérer des objets de document composé. Notez que les mini-serveurs ne peut pas s’exécuter en mode autonome et prennent uniquement en charge les éléments incorporés.|
   |**Serveur complet**|Indique l’application peut créer et gérer des objets de document composé. Serveurs complets sont en mesure d’exécuter en mode autonome et la prise en charge les deux éléments liés et incorporés.|
   |**Conteneur/serveur complet**|Indique que l’application peut être un conteneur et un serveur. Un conteneur est une application qui peut incorporer des éléments liés ou incorporés dans ses propres documents. Un serveur est une application qui peut créer des éléments Automation pour une utilisation par les applications de conteneur.|

- **Options supplémentaires**

   Indique si votre application prend en charge les documents actifs. Consultez [Documents actifs](../../mfc/active-documents.md) pour plus d’informations sur cette fonctionnalité.

   |Option|Description|
   |------------|-----------------|
   |**Serveur de documents actifs**|Indique l’application peut créer et gérer des documents actifs. Si vous sélectionnez cette option, vous devez spécifier une extension de fichier pour votre serveur de documents actifs dans le **extension de fichier** zone le [chaînes modèles de Document](../../mfc/reference/document-template-strings-mfc-application-wizard.md) page de l’Assistant. Consultez [serveurs de documents actifs](../../mfc/active-document-servers.md) pour plus d’informations.|
   |**Conteneur de documents actifs**|Indique que l’application peut contenir des documents actifs dans son cadre. Documents actifs peuvent inclure, par exemple, documents d’Internet Explorer, ou des documents Office telles que les fichiers Microsoft Word ou des feuilles de calcul Excel. Consultez [documents actifs (contenance)](../../mfc/active-document-containment.md) pour plus d’informations.|
   |**Prise en charge des fichiers composés**|Ne sérialise pas les documents de l’application de conteneur en utilisant le format de fichier composé. Cette option force le chargement d’un fichier entier contenant des objets en mémoire. Les enregistrements incrémentiels des objets individuels ne sont pas disponibles. Si un objet est modifié et enregistré par la suite, tous les objets dans le fichier sont enregistrés.|

## <a name="see-also"></a>Voir aussi

[Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md)

