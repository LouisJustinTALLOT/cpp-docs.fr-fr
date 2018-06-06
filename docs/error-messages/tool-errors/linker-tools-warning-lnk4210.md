---
title: LNK4210 d’avertissement des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4210
dev_langs:
- C++
helpviewer_keywords:
- LNK4210
ms.assetid: db48cff8-a2be-4a77-8d03-552b42c228fa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8700d9ad8eeef177de2f70f616cb0c06ba50670
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34703676"
---
# <a name="linker-tools-warning-lnk4210"></a>Avertissement des outils Éditeur de liens LNK4210

> section *section* existe ; il se peut qu’il y ait des terminateurs ou des initialiseurs static non gérés

## <a name="remarks"></a>Notes

Du code a introduit des terminateurs ou des initialiseurs statiques, mais le code de démarrage de bibliothèque VCRuntime ou son équivalent (qui doit exécuter les terminateurs ou des initialiseurs statiques) n’est pas exécuté lorsque l’application démarre. Voici quelques exemples de code qui requiert des terminateurs ou des initialiseurs statiques :

- Variable de classe globale avec un constructeur, un destructeur ou une table de fonctions virtuelles.

- Variable globale initialisée avec une constante au moment de compilation.

Pour résoudre ce problème, essayez l’une des opérations suivantes :

- Supprimez tout le code avec des initialiseurs statiques.

- N’utilisez pas [/NOENTRY](../../build/reference/noentry-no-entry-point.md). Après avoir supprimé /NOENTRY, vous devrez peut-être également supprimer [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) à partir de votre ligne de commande de l’éditeur de liens.

- Si votre build utilise/MT, ajoutez libcmt.lib, libvcruntime.lib et libucrt.lib à votre ligne de commande de l’éditeur de liens. Si votre build utilise /MTd, ajoutez libcmtd.lib, vcruntimed.lib et libucrtd.lib.

- Lors du déplacement de/CLR : pure compilation vers/CLR, supprimez le [/ENTRY](../../build/reference/entry-entry-point-symbol.md) option à partir de la ligne de l’éditeur de liens. Cela permet l’initialisation CRT et les initialiseurs statiques puissent être exécutés au démarrage de l’application. Le **/CLR : pure** option du compilateur est déconseillée dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

Le [/GS](../../build/reference/gs-buffer-security-check.md) option du compilateur exige l’initialisation par le `__security_init_cookie` (fonction). Cette initialisation est fournie par défaut dans le code de démarrage de bibliothèque VCRuntime qui s’exécute dans `_DllMainCRTStartup`.

- Si votre projet est généré à l’aide de /ENTRY et si /ENTRY est passé une fonction autre que `_DllMainCRTStartup`, la fonction doit appeler `_CRT_INIT` pour initialiser la bibliothèque CRT. Cet appel seul n’est pas suffisant si votre DLL utilise/GS, nécessite des initialiseurs statiques ou est appelée dans le contexte du code MFC ou ATL. Consultez [DLL et Visual C++ comportement de la bibliothèque Runtime](../../build/run-time-library-behavior.md) pour plus d’informations.

## <a name="see-also"></a>Voir aussi

- [Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)
