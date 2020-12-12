---
description: 'En savoir plus sur les éléments suivants : avertissement des outils Éditeur de liens LNK4210'
title: Avertissement des outils Éditeur de liens LNK4210
ms.date: 11/04/2016
f1_keywords:
- LNK4210
helpviewer_keywords:
- LNK4210
ms.assetid: db48cff8-a2be-4a77-8d03-552b42c228fa
ms.openlocfilehash: 7634952df026dc664aed2a2f9625a7380b3a38b4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150603"
---
# <a name="linker-tools-warning-lnk4210"></a>Avertissement des outils Éditeur de liens LNK4210

> la *section de section existe ;* Il peut y avoir des initialiseurs statiques non gérés ou des terminateurs

## <a name="remarks"></a>Notes

Du code a introduit des initialiseurs ou des terminateurs statiques, mais le code de démarrage de la bibliothèque VCRuntime ou son équivalent (qui doit exécuter les initialiseurs ou les terminateurs statiques) n’est pas exécuté au démarrage de l’application. Voici quelques exemples de code qui requièrent des initialiseurs statiques ou des terminateurs :

- Variable de classe globale avec un constructeur, un destructeur ou une table de fonctions virtuelles.

- Variable globale initialisée avec une constante de non-compilation.

Pour résoudre ce problème, essayez l’une des opérations suivantes :

- Supprimez tout le code avec des initialiseurs statiques.

- N’utilisez pas [/noentry](../../build/reference/noentry-no-entry-point.md). Après avoir supprimé/NOENTRY, vous devrez peut-être également supprimer [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) de la ligne de commande de l’éditeur de liens.

- Si votre build utilise/MT, ajoutez LIBCMT. lib, libvcruntime. lib et libucrt. lib à la ligne de commande de l’éditeur de liens. Si votre build utilise/MTd, ajoutez LIBCMTD. lib, vcruntimed. lib et libucrtd. lib.

- Quand vous passez de la compilation/CLR : pure à/CLR, supprimez l’option [/entry](../../build/reference/entry-entry-point-symbol.md) de la ligne de l’éditeur de liens. Cela active l’initialisation CRT et permet l’exécution des initialiseurs statiques au démarrage de l’application. L’option de compilateur **/clr : pure** est déconseillée dans visual studio 2015 et n’est pas prise en charge dans visual studio 2017.

L’option de compilateur [/GS](../../build/reference/gs-buffer-security-check.md) requiert l’initialisation par la `__security_init_cookie` fonction. Cette initialisation est fournie par défaut dans le code de démarrage de la bibliothèque VCRuntime qui s’exécute dans `_DllMainCRTStartup` .

- Si votre projet est généré à l’aide de/ENTRY et si/ENTRY reçoit une fonction autre que `_DllMainCRTStartup` , la fonction doit appeler `_CRT_INIT` pour initialiser la bibliothèque CRT. Cet appel seul n’est pas suffisant si votre DLL utilise/GS, requiert des initialiseurs statiques ou est appelé dans le contexte de code MFC ou ATL. Pour plus d’informations, consultez [dll et comportement de la bibliothèque runtime Visual C++](../../build/run-time-library-behavior.md) .

## <a name="see-also"></a>Voir aussi

- [Définition des options de l'Éditeur de liens](../../build/reference/linking.md)
