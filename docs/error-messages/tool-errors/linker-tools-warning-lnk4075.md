---
title: Avertissement des outils Éditeur de liens LNK4075
ms.date: 11/04/2016
f1_keywords:
- LNK4075
helpviewer_keywords:
- LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
ms.openlocfilehash: bf22e7c78dce6949c357d7ad4a0c76209c88eef3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186903"
---
# <a name="linker-tools-warning-lnk4075"></a>Avertissement des outils Éditeur de liens LNK4075

Ignorer l’option « 1 » en raison de la spécification de « option2 »

La deuxième option remplace la première.

Options de l’éditeur de liens qui s’excluent mutuellement sont spécifiées.  Examinez vos options de l’éditeur de liens.  Où les options de l’éditeur de liens sont spécifiées dépend de la façon dont vous générez votre projet.

- Si vous générez dans l’environnement de développement, recherchez dans les pages de propriétés de l’éditeur de liens pour votre projet et voir où les deux options de l’éditeur de liens sont spécifiées.  Consultez [définir du compilateur et les propriétés de build](../../build/working-with-project-properties.md) pour plus d’informations.

- Si vous générez à la ligne de commande, consultez les options de l’éditeur de liens spécifiées.

- Si vous générez des scripts de build, examinez vos scripts pour voir où ces options de l’éditeur de liens sont spécifiées.

Lorsque vous trouvez où les options de l’éditeur de liens qui s’excluent mutuellement sont spécifiées, supprimez l’une des options de l’éditeur de liens.

Voici quelques exemples spécifiques :

- Si vous liez un module qui a été compilé avec **/Zi**, ce qui implique une option de l’éditeur de liens interne appelée /EDITANDCONTINUE et un module qui a été compilé avec/OPT : REF, / OPT : ICF ou/INCREMENTAL : no, ce qui n’implique aucune option /EDITANDCONTINUE. la solution, vous allez obtenir LNK4075.  Consultez [/Z7, / Zi, /ZI (Format des informations de débogage)](../../build/reference/z7-zi-zi-debug-information-format.md) pour plus d’informations.