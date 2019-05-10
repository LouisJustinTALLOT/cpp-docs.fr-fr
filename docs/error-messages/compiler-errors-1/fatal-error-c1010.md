---
title: Erreur irrécupérable C1010
ms.date: 11/04/2016
f1_keywords:
- C1010
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
ms.openlocfilehash: 204c7ef94d82513338f6635ec9eb22f26fc090a7
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448021"
---
# <a name="fatal-error-c1010"></a>Erreur irrécupérable C1010

fin de fichier inattendue lors de la recherche d'un en-tête précompilé. Avez-vous oublié d’ajouter ' #include nom » à votre source ?

Un fichier include spécifié avec [/Yu](../../build/reference/yu-use-precompiled-header-file.md) n’est pas répertorié dans le fichier source.  Cette option est activée par défaut dans la plupart des Visual Studio C++ « stdafx.h » et les types de projet est la valeur par défaut incluent le fichier spécifié par cette option.

Dans l’environnement Visual Studio, utilisez une des méthodes suivantes pour résoudre cette erreur :

- Si vous n’utilisez pas d’en-têtes précompilés dans votre projet, définissez le **créer/utiliser un en-tête précompilé** propriété des fichiers sources à **sans utiliser les en-têtes précompilés**. Pour définir cette option du compilateur, procédez comme suit :

   1. Dans le volet Explorateur de solutions du projet, cliquez sur le nom de projet, puis cliquez sur **propriétés**.

   1. Dans le volet gauche, cliquez sur le **C/C++** dossier.

   1. Cliquez sur le **en-têtes précompilés** nœud.

   1. Dans le volet droit, cliquez sur **Création/utilisation d’un en-tête précompilé**, puis cliquez sur **pas utiliser les en-têtes précompilés**.

- Assurez-vous que pas accidentellement supprimé, renommé ou supprimé le fichier d’en-tête (par défaut, stdafx.h) à partir du projet actuel. Ce fichier doit également être inclus avant tout autre code dans vos fichiers sources à l’aide de **#include « stdafx.h »**. (Ce fichier d’en-tête est spécifié en tant que **Création/utilisation PCH via fichier** propriété du projet)