---
description: 'En savoir plus sur : relation contenant-contenu de document actif'
title: Relation contenant-contenu de document actif
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- MFC, COM support
- active document containers [MFC], about active document containers
- MFC COM, active document containment
ms.assetid: b8dfa74b-75ce-47df-b75e-fc87b7f7d687
ms.openlocfilehash: 9a190e0203152e2411699aa601a095a530303546
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150382"
---
# <a name="active-document-containment"></a>Relation contenant-contenu de document actif

La relation contenant-contenu de document actif est une technologie qui fournit une image unique dans laquelle travailler avec des documents, au lieu de vous contraindre à créer et à utiliser plusieurs frames d’application pour chaque type de document. Il diffère de la technologie OLE de base dans le sens où OLE fonctionne avec des objets incorporés dans un document composé dans lequel une seule partie du contenu peut être active. Avec la relation contenant-contenu de document actif, vous activez un document entier (c’est-à-dire, une application entière, y compris des menus associés, des barres d’outils, etc.) dans le contexte d’une image unique.

La technologie de relation contenant-contenu de document actif a été développée à l’origine pour Microsoft Office mettre en œuvre le classeur Office. Toutefois, la technologie est suffisamment flexible pour prendre en charge les conteneurs de documents actifs autres que le classeur Office et peut prendre en charge des serveurs de documents autres que des applications compatibles Office et Office.

L’application qui héberge des documents actifs est appelée un [conteneur de documents actifs](active-document-containers.md). Les exemples de ces conteneurs sont le classeur Microsoft Office ou Microsoft Internet Explorer.

La relation contenant-contenu de document actif est implémentée sous la forme d’un ensemble d’extensions pour les documents OLE, la technologie de document composé d’OLE. Les extensions sont des interfaces supplémentaires qui permettent à un objet sur place incorporable de représenter un document entier plutôt qu’un seul élément de contenu incorporé. Comme avec les documents OLE, la relation contenant-contenu de document actif utilise un conteneur qui fournit l’espace d’affichage pour les documents actifs et les serveurs qui fournissent l’interface utilisateur et les fonctionnalités de manipulation pour les documents actifs eux-mêmes.

Un [serveur de documents actif](active-document-servers.md) est une application (telle que Word, Excel ou PowerPoint) qui prend en charge une ou plusieurs classes de document actives, où chaque objet lui-même prend en charge les interfaces d’extension qui autorisent l’activation de l’objet dans un conteneur approprié.

Un [document actif](active-documents.md) (fourni à partir d’un serveur de documents actif, tel que Word ou Excel) est essentiellement un document conventionnel à l’échelle complète qui est incorporé en tant qu’objet dans un autre conteneur de documents actifs. Contrairement aux objets incorporés, les documents actifs disposent d’un contrôle total sur leurs pages, et l’interface complète de l’application (avec tous ses outils et commandes sous-jacents) est à la disposition de l’utilisateur pour les modifier.

Pour mieux comprendre un document actif, vous le distinguez d’un objet OLE incorporé standard. À la suite de la Convention OLE, un objet incorporé est un objet qui est affiché dans la page du document qui le possède et le document est géré par un conteneur OLE. Le conteneur stocke les données de l’objet incorporé avec le reste du document. Toutefois, les objets incorporés sont limités dans le fait qu’ils ne contrôlent pas la page sur laquelle ils apparaissent.

Les utilisateurs d’une application de conteneur de documents actifs peuvent créer des documents actifs (appelés sections dans le classeur Office) à l’aide de leurs applications favorites (à condition que ces applications soient activées pour les documents actifs), mais les utilisateurs peuvent gérer le projet résultant en tant qu’entité unique, qui peut être nommée de manière unique, enregistrée, imprimée, etc. De la même façon, un utilisateur d’un navigateur Internet peut traiter l’ensemble du réseau, ainsi que des systèmes de fichiers locaux, comme une entité de stockage de documents unique, avec la possibilité de parcourir les documents de ce stockage à partir d’un emplacement unique.

## <a name="sample-programs"></a>Exemples de programmes

- L’exemple [MFCBIND](../overview/visual-cpp-samples.md) illustre l’implémentation d’une application de conteneur de documents actifs.

## <a name="see-also"></a>Voir aussi

[MFC COM](mfc-com.md)
