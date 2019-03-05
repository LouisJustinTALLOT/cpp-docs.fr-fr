---
title: Relation contenant-contenu de document actif
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- MFC, COM support
- active document containers [MFC], about active document containers
- MFC COM, active document containment
ms.assetid: b8dfa74b-75ce-47df-b75e-fc87b7f7d687
ms.openlocfilehash: 1811febdb26091785f8b709e90f8cdd7a7f8afdd
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258292"
---
# <a name="active-document-containment"></a>Relation contenant-contenu de document actif

Relation contenant-contenu de document actif est une technologie qui fournit un frame unique permettant de travailler avec des documents, au lieu de vous obliger à créer et utiliser plusieurs frames d’application pour chaque type de document. Elle est différente de la technologie OLE de base OLE fonctionne avec des objets incorporés dans un document composé dans lequel seule une partie du contenu peut être active. Avec relation contenant-contenu de document actif, vous activez un document entier (autrement dit, une application entière, y compris associés menus, barres d’outils et ainsi de suite) dans le contexte d’une seule image.

La technologie de relation contenant-contenu de document actif a été développée pour Microsoft Office doivent implémenter le classeur Office. Toutefois, la technologie est suffisamment flexible pour prendre en charge des conteneurs de documents actifs autres que le classeur Office et peut prendre en charge les serveurs de documents autres que les applications Office et compatible avec Office.

L’application qui héberge les documents actifs est appelée un [conteneur de documents actifs](../mfc/active-document-containers.md). Exemples de ces conteneurs sont le classeur Microsoft Office ou Microsoft Internet Explorer.

Relation contenant-contenu de document actif est implémenté comme un ensemble d’extensions vers OLE de documents, la technologie de document composé OLE. Les extensions sont des interfaces supplémentaires qui permettent à un objet intégrable, sur place représenter un document entier au lieu d’un seul élément de contenu incorporé. Comme avec les documents OLE, la relation contenant-contenu de document actif utilise un conteneur qui fournit l’espace d’affichage pour les documents actifs et les serveurs qui fournissent des fonctionnalités de manipulation et d’interface de l’utilisateur pour les documents actifs eux-mêmes.

Un [serveur de documents actifs](../mfc/active-document-servers.md) est une application (par exemple, Word, Excel ou PowerPoint) qui prend en charge une ou plusieurs classes de document actif, où chaque objet lui-même prend en charge les interfaces d’extension qui permettent à l’objet à activer dans un conteneur approprié.

Un [document actif](../mfc/active-documents.md) (fourni à partir d’un serveur de documents actifs tels que Word ou Excel) est essentiellement un document à grande échelle, conventionnel qui est incorporé en tant qu’objet dans un autre conteneur de documents actifs. Contrairement aux objets incorporés, les documents actifs contrôlent complètement leurs pages, et l’interface complète de l’application (avec toutes ses sous-jacente commandes et outils) est disponible à l’utilisateur pour les modifier.

Un document actif permet de mieux comprendre le comparer à partir d’un objet incorporé OLE standard. Suivre la convention OLE, un objet incorporé est un qui s’affiche dans la page du document auquel il appartient, et le document est géré par un conteneur OLE. Le conteneur stocke les données de l’objet incorporé avec le reste du document. Toutefois, les objets incorporés sont limitées dans la mesure où ils ne contrôlent pas la page sur laquelle ils apparaissent.

Les utilisateurs d’une application de conteneur de documents actifs peuvent créer des documents actifs (appelés sections dans le classeur Office) à l’aide de leurs applications favorites (à condition que ces applications sont compatibles document actif), mais les utilisateurs peuvent gérer le projet résultant comme une une entité unique, ce qui peut porter un nom unique, enregistré, imprimé, et ainsi de suite. Dans la même façon, un utilisateur d’un navigateur Internet peut traiter l’ensemble du réseau, ainsi que les systèmes de fichiers locaux, comme une entité de stockage de document unique avec la possibilité de parcourir les documents dans ce stockage depuis un emplacement unique.

## <a name="sample-programs"></a>Exemples de programmes

- Le [MFCBIND](../visual-cpp-samples.md) exemple illustre l’implémentation d’une application de conteneur de documents actifs.

## <a name="see-also"></a>Voir aussi

[MFC COM](../mfc/mfc-com.md)
