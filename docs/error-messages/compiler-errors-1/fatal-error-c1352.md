---
description: 'En savoir plus sur : erreur irrécupérable C1352'
title: Erreur irrécupérable C1352
ms.date: 11/04/2016
f1_keywords:
- C1352
helpviewer_keywords:
- C1352
ms.assetid: d044e8b0-b6ef-4d57-8eb5-6254071be707
ms.openlocfilehash: 6838d3e095616d576ff1a709d4d82f879eb9e464
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276554"
---
# <a name="fatal-error-c1352"></a>Erreur irrécupérable C1352

Code MSIL non valide ou endommagé dans la fonction 'fonction' à partir de 'fichier' de module

Un fichier .netmodule a été passé au compilateur, mais le compilateur a détecté que le fichier était endommagé.  Demandez à l’auteur du fichier .netmodule de rechercher l’origine du problème.

Le compilateur ne recherche pas tous les types d’endommagements dans les fichiers .netmodule qu’il vérifie.  Toutefois, il vérifie que tous les chemins de contrôle d’une fonction contiennent bien une instruction return.

Pour plus d’informations, consultez [Fichiers .netmodule en tant qu’entrée de l’Éditeur de liens](../../build/reference/netmodule-files-as-linker-input.md).
