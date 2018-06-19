---
title: Prise en charge de l’utilisation de wmain | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- wWinMain
dev_langs:
- C++
helpviewer_keywords:
- wide characters [C++], wmain function
- wWinMain function
- wmain function
ms.assetid: 41213c41-668c-40a4-8a1e-77d9eded720d
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c8b82b9f13da1b7c4884001fed5afce832147714
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856486"
---
# <a name="support-for-using-wmain"></a>Prise en charge de l'utilisation de wmain
Visual C++ prend en charge la définition d’un **wmain** de fonction et de passer des arguments à caractère élargi à votre application Unicode. Vous déclarez des paramètres formels à **wmain**, à l’aide d’un format similaire à **principal**. Vous pouvez ensuite passer des arguments à caractère élargi et éventuellement un pointeur d’environnement à caractère élargi au programme. Les paramètres `argv` et `envp` de la fonction **wmain** sont de type `wchar_t*`. Par exemple :  
  
```  
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )  
```  
  
> [!NOTE]
>  Les applications Unicode MFC utilisent **wWinMain** comme point d’entrée. Dans ce cas, `CWinApp::m_lpCmdLine` est une chaîne Unicode. Veillez à définir **wWinMainCRTStartup** avec la [/ENTRY](../build/reference/entry-entry-point-symbol.md) option de l’éditeur de liens.  
  
 Si votre programme utilise une fonction **main**, l'environnement de caractère multioctets est créé par la bibliothèque Runtime au démarrage du programme. Une copie de l'environnement à caractère élargi est créée uniquement lorsqu'elle est nécessaire (par exemple, par un appel des fonctions `_wgetenv` ou `_wputenv`). Le premier appel à `_wputenv`, ou sur le premier appel à `_wgetenv` si un environnement MBCS existe déjà, un environnement de chaîne à caractères larges correspondant est créé. L’environnement est ensuite vers lequel pointe le `_wenviron` variable globale, ce qui est une version à caractères larges de la `_environ` (variable globale). À ce stade, les deux copies de l’environnement (MBCS et Unicode) existent simultanément et sont conservées par le système d’exécution pendant toute la vie du programme.  
  
 De même, si votre programme utilise une fonction **wmain**, un environnement à caractère élargi est créé au moment du démarrage et une variable globale `_wenviron` pointe vers cet environnement. Un environnement MBCS (ASCII) est créé sur le premier appel à `_putenv` ou `getenv` et est désigné par le `_environ` (variable globale).  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge Unicode](../text/support-for-unicode.md)   
 [Synthèse de la programmation Unicode](../text/unicode-programming-summary.md)   
 [Fonction WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559)