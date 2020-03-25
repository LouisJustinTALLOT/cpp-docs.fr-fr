---
title: Erreur des outils Éditeur de liens LNK1302
ms.date: 11/04/2016
f1_keywords:
- LNK1302
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
ms.openlocfilehash: 8323fa234851ce3ba12083adb74d5ee0fba0ac69
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194926"
---
# <a name="linker-tools-error-lnk1302"></a>Erreur des outils Éditeur de liens LNK1302

ne prennent en charge que la liaison de. netmodule sécurisés ; Impossible de lier le fichier. netmodule

Un. netmodule (compilé avec **/LN**) a été passé à l’éditeur de liens dans une tentative de l’utilisateur d’appeler la liaison MSIL.  Un C++ module est valide pour la liaison MSIL s’il est compilé avec **/clr : safe**.

Pour corriger cette erreur, compilez avec **/clr : safe** pour activer la liaison MSIL, ou transmettez le fichier **/CLR** ou **/clr : pure** . obj à l’éditeur de liens au lieu du module.

Pour plus d'informations, consultez la rubrique

- [/LN (Créer le module MSIL)](../../build/reference/ln-create-msil-module.md)

- [Fichiers .netmodule en tant qu’entrée de l’Éditeur de liens](../../build/reference/netmodule-files-as-linker-input.md)
