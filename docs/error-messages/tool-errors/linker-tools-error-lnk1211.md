---
title: "Erreur LNK1211 des outils Éditeur de liens | Documents Microsoft"
ms.date: 12/05/2017
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1211
dev_langs: C++
helpviewer_keywords: LNK1211
ms.assetid: 607400eb-4180-4892-817f-eedfa628af61
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 51150fb2a57f48f04cca97e5f16fe1a28ead2c50
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1211"></a>Erreur des outils Éditeur de liens LNK1211

> informations de type précompilé non trouvées ; '*nom de fichier*' non lié ou remplacé

Le *nom de fichier* fichier objet compilé à l’aide de [/Yc](../../build/reference/yc-create-precompiled-header-file.md), n’a pas été spécifié dans la commande LINK ou a été remplacé.

Si vous créez une bibliothèque de débogage qui utilise des en-têtes précompilés et si vous spécifiez **/Yc** et [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), Visual C++ génère un fichier objet précompilé qui contient des informations de débogage. L’erreur produit uniquement lorsque vous stockez le fichier objet précompilé dans une bibliothèque, utilisez la bibliothèque pour construire une image exécutable et les fichiers d’objets qui sont référencés n’ont aucune référence transitive à toutes les fonctions que le fichier objet précompilé définit.

Il existe deux méthodes pour contourner cette situation :

- Spécifiez le [/Yd](../../build/reference/yd-place-debug-information-in-object-file.md) option du compilateur pour ajouter les informations de débogage à partir de l’en-tête précompilé à chaque module objet. Cette méthode est la moins recommandée, car elle produit généralement des modules d’objets volumineux qui peuvent augmenter le temps nécessaire pour lier l’application.

- Spécifiez [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) et passez le nom d’une chaîne arbitraire, lorsque vous créez un fichier d’en-tête précompilé qui ne contient-elle pas toutes les définitions de fonction. Cela indique au compilateur pour créer un symbole dans le fichier objet précompilé et à émettre une référence à ce symbole dans chaque fichier objet utilisant le fichier d’en-tête précompilé qui est associé au fichier objet précompilé.

Lorsque vous compilez un module avec **/Yc** et **/Yl**, le compilateur crée un symbole semblable à `__@@_PchSym_@00@...@symbol_name`, où les points de suspension (...) représente une chaîne de caractères générée par le compilateur et le stocke dans le module de l’objet. N’importe quel fichier source que vous compilez avec cet en-tête précompilé fait référence au symbole spécifié, ce qui entraîne l’éditeur de liens à inclure le module objet et ses informations de débogage à partir de la bibliothèque.
