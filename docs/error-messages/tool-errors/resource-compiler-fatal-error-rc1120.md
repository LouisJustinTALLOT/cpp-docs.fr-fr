---
title: Erreur irrécupérable RC1120 du compilateur de ressources
ms.date: 11/04/2016
f1_keywords:
- RC1120
helpviewer_keywords:
- RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
ms.openlocfilehash: 855a76ff63145695a7063944701d7acc684e0084
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173008"
---
# <a name="resource-compiler-fatal-error-rc1120"></a>Erreur irrécupérable RC1120 du compilateur de ressources

mémoire insuffisante, nombre d’octets requis

Le compilateur de ressources n’a pas pu stocker les éléments qu’il stocke dans son tas. En général, il s’agit du résultat d’un trop grand nombre de symboles.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Augmentez l’espace du fichier d’échange Windows. Pour plus d’informations sur l’extension de l’espace de fichier d’échange, consultez mémoire virtuelle dans l’aide de Windows.

1. Éliminez les fichiers include inutiles, en particulier les `#define`s et les prototypes de fonction inutiles.

1. Fractionnez le fichier actuel en deux fichiers ou plus et compilez-les séparément.

1. Supprimer les autres programmes ou pilotes en cours d’exécution dans le système, ce qui peut consommer une quantité importante de mémoire.
