---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK1211'
title: Erreur des outils Éditeur de liens LNK1211
ms.date: 12/05/2017
f1_keywords:
- LNK1211
helpviewer_keywords:
- LNK1211
ms.assetid: 607400eb-4180-4892-817f-eedfa628af61
ms.openlocfilehash: d3201055643f5874ccc319f04fb6eb2d976bf67f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341618"
---
# <a name="linker-tools-error-lnk1211"></a>Erreur des outils Éditeur de liens LNK1211

> informations de type précompilé introuvables ; '*nom_fichier*'n’est pas lié ou remplacé

Le fichier objet *filename* , compilé à l’aide de [/Yc](../../build/reference/yc-create-precompiled-header-file.md), n’a pas été spécifié dans la commande LINK ou a été remplacé.

Si vous créez une bibliothèque de débogage qui utilise des en-têtes précompilés et si vous spécifiez **/Yc** et [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), Visual C++ génère un fichier objet précompilé qui contient des informations de débogage. L’erreur se produit uniquement lorsque vous stockez le fichier objet précompilé dans une bibliothèque, que vous utilisez la bibliothèque pour générer une image exécutable, et que les fichiers objets référencés n’ont pas de références transitives aux fonctions définies par le fichier objet précompilé.

Il existe deux méthodes pour contourner cette situation :

- Spécifiez l’option du compilateur [/Yd](../../build/reference/yd-place-debug-information-in-object-file.md) pour ajouter les informations de débogage de l’en-tête précompilé à chaque module objet. Cette méthode est moins souhaitable car elle produit généralement des modules d’objets volumineux qui peuvent augmenter le temps nécessaire pour lier l’application.

- Spécifiez [/yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) et transmettez le nom d’une chaîne arbitraire quand vous créez un fichier d’en-tête précompilé qui ne contient aucune définition de fonction. Cela indique au compilateur de créer un symbole dans le fichier objet précompilé et d’émettre une référence à ce symbole dans chaque fichier objet qui a utilisé le fichier d’en-tête précompilé associé au fichier objet précompilé.

Quand vous compilez un module avec **/Yc** et **/yl**, le compilateur crée un symbole semblable à `__@@_PchSym_@00@...@symbol_name` , où les points de suspension (...) représentent une chaîne de caractères générée par le compilateur et le stocke dans le module objet. Tout fichier source que vous compilez avec cet en-tête précompilé fait référence au symbole spécifié, ce qui amène l’éditeur de liens à inclure le module objet et ses informations de débogage à partir de la bibliothèque.
