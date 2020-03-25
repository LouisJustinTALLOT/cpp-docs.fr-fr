---
title: Avertissement des outils Éditeur de liens LNK4075
ms.date: 11/04/2016
f1_keywords:
- LNK4075
helpviewer_keywords:
- LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
ms.openlocfilehash: e4a385b9559e2f54e81bda76e6dd13505e978a74
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183486"
---
# <a name="linker-tools-warning-lnk4075"></a>Avertissement des outils Éditeur de liens LNK4075

« option1 » ignoré en raison de la spécification « option2 »

La deuxième option remplace la première.

Des options de l’éditeur de liens s’excluent mutuellement sont spécifiées.  Examinez les options de l’éditeur de liens.  La spécification des options de l’éditeur de liens dépend de la façon dont vous générez votre projet.

- Si vous générez dans l’environnement de développement, recherchez dans les pages de propriétés de l’éditeur de liens pour votre projet et vérifiez où les deux options de l’éditeur de liens sont spécifiées.  Pour plus d’informations, consultez [définir les propriétés de compilation et de génération](../../build/working-with-project-properties.md) .

- Si vous générez à partir de la ligne de commande, examinez les options de l’éditeur de liens spécifiées ici.

- Si vous générez avec des scripts de build, examinez vos scripts pour voir où ces options de l’éditeur de liens sont spécifiées.

Lorsque vous trouvez où les options de l’éditeur de liens s’excluent mutuellement, supprimez l’une des options de l’éditeur de liens.

Exemples spécifiques :

- Si vous liez un module qui a été compilé avec **/Zi**, ce qui implique une option interne de l’éditeur de liens appelée/EDITANDCONTINUE et un module qui a été compilé avec/OPT : REF,/opt : ICF ou/INCREMENTAL : no, qui n’implique aucun/EDITANDCONTINUE, vous obtiendrez LNK4075.  Pour plus d’informations [, consultez/Z7,/Zi,/ZI (format des informations de débogage)](../../build/reference/z7-zi-zi-debug-information-format.md) .
