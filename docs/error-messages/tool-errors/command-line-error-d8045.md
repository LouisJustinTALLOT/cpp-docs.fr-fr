---
title: Erreur de ligne de commande D8045
ms.date: 11/04/2016
f1_keywords:
- D8045
helpviewer_keywords:
- D8045
ms.assetid: 01c8808c-bac1-4b4d-8a90-b595f95e9318
ms.openlocfilehash: 7964c2539b5358d2d946e530c4ee75110857446d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214194"
---
# <a name="command-line-error-d8045"></a>Erreur de ligne de commande D8045

Impossible de compiler le fichier C 'fichier' avec l’option /clr

Uniquement les fichiers de code source C++ peuvent être passés à une compilation qui utilise **/CLR**.  Utilisez **/TP** pour compiler un fichier .c en tant que fichier .cpp ; consultez [TP, / TP, /TP (spécifier le Type des fichiers Source)](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) pour plus d’informations.

Pour plus d’informations, consultez l’article [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

D8045 peut également se produire si vous compilez une application ATL à l’aide de Visual C++. Voir [Guide pratique pour Migrer vers/CLR](../../dotnet/how-to-migrate-to-clr.md) pour plus d’informations.