---
title: R6030 d’erreur d’exécution C | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6030
dev_langs:
- C++
helpviewer_keywords:
- R6030
ms.assetid: 0238a6c3-a033-4046-8adc-f8f99d961153
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae8eb17fc9d074604586582be08c43289b680b4f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299534"
---
# <a name="c-runtime-error-r6030"></a>R6030 d’erreur d’exécution C
CRT non initialisé  
  
> [!NOTE]
>  Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car il a un problème interne. Ce problème est généralement dû à certains programmes de logiciels de sécurité, ou rarement, par un bogue dans le programme.  
>   
>  Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :  
>   
>  -   Votre logiciel de sécurité peut-être avoir des instructions spécifiques pour atténuer ce problème. Vérification du site Web de votre fournisseur de logiciels de sécurité pour plus d’informations. Vous pouvez également vérifier les versions mises à jour de votre logiciel de sécurité, ou essayez de logiciels de sécurité différents.  
> -   Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour réparer ou réinstaller le programme.  
> -   Vérifiez **mise à jour Windows** dans les **le panneau de configuration** pour les mises à jour logicielles.  
> -   Recherchez une version mise à jour de l’application. Si le problème persiste, contactez le fournisseur de l’application.  
  
 **Informations pour les programmeurs**  
  
 Cette erreur se produit si vous utilisez le Runtime C (CRT), mais le code de démarrage du CRT n’a pas été exécuté. Il est possible d’obtenir cette erreur si le commutateur de l’éditeur de liens [/ENTRY](../../build/reference/entry-entry-point-symbol.md) est utilisée pour remplacer la valeur par défaut à partir de l’adresse, généralement **mainCRTStartup**, **wmainCRTStartup** pour un console EXE, **WinMainCRTStartup** ou **wWinMainCRTStartup** pour un EXE Windows, ou **_DllMainCRTStartup** pour une DLL. Sauf si l’une des fonctions ci-dessus est appelée au démarrage, le Runtime C ne sera pas initialisé. Ces fonctions de démarrage sont généralement appelées par défaut lorsque vous créer un lien vers la bibliothèque runtime C et que vous utilisez la normale **principal**, **wmain**, **WinMain**, ou  **DllMain** points d’entrée.  
  
 Il est également possible d’obtenir cette erreur quand un autre programme utilise des techniques d’injection de code pour intercepter certains appels de bibliothèque DLL. Certains programmes de sécurité contraignant utilisent cette technique. Dans les versions de Visual C++ antérieures à Visual Studio 2015, il est possible d’utiliser une bibliothèque CRT liée statiquement pour résoudre le problème, mais cela n’est pas recommandé pour des raisons de sécurité et application des mises à jour. Correction de ce problème peut nécessiter l’action de l’utilisateur final.