---
title: Erreur irrécupérable C1010
ms.date: 08/19/2019
f1_keywords:
- C1010
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
ms.openlocfilehash: 35b0f60f7eb3be887598e7ffaf3e3eae74aefcff
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630788"
---
# <a name="fatal-error-c1010"></a>Erreur irrécupérable C1010

fin de fichier inattendue lors de la recherche d'un en-tête précompilé. Avez-vous oublié d’ajouter' #include Name’à votre source?

Un fichier include spécifié avec [/Yu](../../build/reference/yu-use-precompiled-header-file.md) n’est pas listé dans le fichier source.  Cette option est activée par défaut dans la plupart des C++ types de projets Visual Studio et *pch. h* (*stdafx. h* dans Visual Studio 2017 et versions antérieures) est le fichier include par défaut spécifié par cette option.

Dans l’environnement Visual Studio, utilisez l’une des méthodes suivantes pour résoudre cette erreur:

- Si vous n’utilisez pas d’en-têtes précompilés dans votre projet, affectez à la propriété **créer/utiliser un en-tête précompilé** des fichiers sources la valeur **n’utilisant pas les en-têtes**précompilés. Pour définir cette option du compilateur, procédez comme suit:

   1. Dans le volet Explorateur de solutions du projet, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Propriétés**.

   1. Dans le volet gauche, cliquez sur le dossier **C/C++**  .

   1. Cliquez sur le nœud **en-têtes** précompilés.

   1. Dans le volet droit, cliquez sur **créer/utiliser un en-tête précompilé**, puis sur **ne pas utiliser les en-têtes**précompilés.

- Assurez-vous que vous n’avez pas supprimé par inadvertance, renommé ou supprimé le fichier d’en-tête (par défaut, stdafx. h) du projet actuel. Ce fichier doit également être inclus avant tout autre code dans vos fichiers sources à l’aide de **#include «stdafx. h»** . (Ce fichier d’en-tête est spécifié en tant que propriété de projet **créer/utiliser PCH par fichier** )