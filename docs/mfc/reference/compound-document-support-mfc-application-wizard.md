---
description: 'En savoir plus sur : prise en charge des documents composés, Assistant Application MFC'
title: Prise en charge des documents composés, Assistant Application MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.compdoc
ms.assetid: 42e1af83-12c4-438d-92eb-13835afdb148
ms.openlocfilehash: 5ccd95812c7b8a4379528b4c784a3d7ca09f538f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331363"
---
# <a name="compound-document-support-mfc-application-wizard"></a>Prise en charge des documents composés, Assistant Application MFC

Dans cette page de l’Assistant Application MFC, indiquez le niveau auquel votre application fournit la prise en charge des documents composites et actifs. Votre application doit prendre en charge l’architecture document/vue pour la prise en charge des documents composés et des modèles de document.

Par défaut, l’application ne contient aucune prise en charge des documents composés. Si vous acceptez ce paramètre par défaut, votre application ne peut pas prendre en charge les documents ou les fichiers composés actifs.

- **Prise en charge des documents composés**

  Détermine si votre application fournit la prise en charge des conteneurs, la prise en charge du serveur ou les deux. Pour plus d’informations sur cette zone, consultez :

  - [Conteneurs : implémentation d’un conteneur](../../mfc/containers-implementing-a-container.md)

  - [Serveurs : implémentation d’un serveur](../../mfc/servers-implementing-a-server.md)

  |Option|Description|
  |------------|-----------------|
  |**Aucun**|Indique l’absence de prise en charge de la liaison et de l’incorporation d’objets (OLE). Par défaut, l’Assistant application crée une application sans prise en charge ActiveX.|
  |**Conteneur**|Contient des objets liés et incorporés.|
  |**Mini-serveur**|Indique que l’application peut créer et gérer des objets de document composé. Notez que les mini-serveurs ne peuvent pas s’exécuter en mode autonome et ne prennent en charge que les éléments incorporés.|
  |**Serveur complet**|Indique que l’application peut créer et gérer des objets de document composé. Les serveurs complets peuvent s’exécuter en mode autonome et prendre en charge les éléments liés et incorporés.|
  |**Conteneur/serveur complet**|Indique que l’application peut être à la fois un conteneur et un serveur. Un conteneur est une application qui peut incorporer des éléments incorporés ou liés dans ses propres documents. Un serveur est une application qui peut créer des éléments d’automatisation pour une utilisation par les applications de conteneur.|

- **Options supplémentaires**

  Indique si votre application prend en charge les documents actifs. Pour plus d’informations sur cette fonctionnalité, consultez [documents actifs](../../mfc/active-documents.md) .

  |Option|Description|
  |------------|-----------------|
  |**Serveur de documents actifs**|Indique que l’application peut créer et gérer des documents actifs. Si vous sélectionnez cette option, vous devez spécifier une extension de fichier pour votre serveur de documents actifs dans la zone **extension de fichier** de la page chaînes de [modèle de document](../../mfc/reference/document-template-strings-mfc-application-wizard.md) de l’Assistant. Pour plus d’informations, consultez [serveurs de documents actifs](../../mfc/active-document-servers.md) .|
  |**Conteneur de documents actifs**|Indique que l’application peut contenir des documents actifs dans son cadre. Les documents actifs peuvent inclure, par exemple, des documents Internet Explorer ou des documents Office, tels que des fichiers Microsoft Word ou des feuilles de calcul Excel. Pour plus d’informations, consultez [relation contenant-contenu de document actif](../../mfc/active-document-containment.md) .|
  |**Prise en charge des fichiers composés**|Ne sérialise pas les documents de l’application conteneur à l’aide du format de fichier composé. Cette option force le chargement d’un fichier entier contenant des objets en mémoire. Les enregistrements incrémentiels dans des objets individuels ne sont pas disponibles. Si un objet est modifié et enregistré par la suite, tous les objets du fichier sont enregistrés.|

## <a name="see-also"></a>Voir aussi

[Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md)
