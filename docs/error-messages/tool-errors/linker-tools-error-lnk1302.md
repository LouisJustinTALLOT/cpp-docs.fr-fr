---
title: Erreur des outils Éditeur de liens LNK1302
ms.date: 11/04/2016
f1_keywords:
- LNK1302
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
ms.openlocfilehash: c3b1117b31db4759b385943323a581da7a58f0c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160443"
---
# <a name="linker-tools-error-lnk1302"></a>Erreur des outils Éditeur de liens LNK1302

uniquement prise en charge de liaison de .netmodules sécurisés ; Impossible de lier le fichier .netmodule

Un fichier .netmodule (compilé avec **/LN**) a été passé à l’éditeur de liens dans un utilisateur tente d’appeler la liaison MSIL.  Un module C++ est valide pour la liaison MSIL s’il est compilé avec **/CLR : safe**.

Pour corriger cette erreur, compilez avec **/CLR : safe** afin d’activer la liaison MSIL ou passez le **/CLR** ou **/CLR : pure** fichier .obj afin de l’éditeur de liens au lieu du module.

Pour plus d'informations, consultez

- [/LN (Créer le module MSIL)](../../build/reference/ln-create-msil-module.md)

- [Fichiers .netmodule en tant qu’entrée de l’Éditeur de liens](../../build/reference/netmodule-files-as-linker-input.md)