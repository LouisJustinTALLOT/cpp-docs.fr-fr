---
description: 'En savoir plus sur : prise en charge de l’utilisation de wmain'
title: Prise en charge de l'utilisation de wmain
ms.date: 11/04/2016
f1_keywords:
- wWinMain
helpviewer_keywords:
- wide characters [C++], wmain function
- wWinMain function
- wmain function
ms.assetid: 41213c41-668c-40a4-8a1e-77d9eded720d
ms.openlocfilehash: b6a954ab62c9bc675bd2b71275d615b3ee4c1376
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335741"
---
# <a name="support-for-using-wmain"></a>Prise en charge de l'utilisation de wmain

Visual C++ prend en charge la définition d’une fonction **wmain** et le passage d’arguments à caractères larges à votre application Unicode. Vous déclarez des paramètres formels sur **wmain**, à l’aide d’un format semblable à `main` . Vous pouvez ensuite passer des arguments à caractère élargi et éventuellement un pointeur d’environnement à caractère élargi au programme. Les paramètres `argv` et `envp` de la fonction **wmain** sont de type `wchar_t*`. Par exemple :

```cpp
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )
```

> [!NOTE]
> Les applications Unicode MFC utilisent `wWinMain` comme point d’entrée. Dans ce cas, `CWinApp::m_lpCmdLine` est une chaîne Unicode. Veillez à définir `wWinMainCRTStartup` avec l’option de l’éditeur de liens [/entry](../build/reference/entry-entry-point-symbol.md) .

Si votre programme utilise une fonction **main**, l'environnement de caractère multioctets est créé par la bibliothèque Runtime au démarrage du programme. Une copie de l'environnement à caractère élargi est créée uniquement lorsqu'elle est nécessaire (par exemple, par un appel des fonctions `_wgetenv` ou `_wputenv`). Lors du premier appel à `_wputenv` , ou lors du premier appel à `_wgetenv` si un environnement MBCS existe déjà, un environnement de chaîne à caractères larges correspondant est créé. L’environnement est ensuite désigné par la `_wenviron` variable globale, qui est une version à caractères larges de la `_environ` variable globale. À ce stade, deux copies de l’environnement (MBCS et Unicode) existent simultanément et sont gérées par le système d’exécution tout au long de la durée de vie du programme.

De même, si votre programme utilise une fonction **wmain**, un environnement à caractère élargi est créé au moment du démarrage et une variable globale `_wenviron` pointe vers cet environnement. Un environnement MBCS (ASCII) est créé lors du premier appel à `_putenv` ou `getenv` , et est désigné par la `_environ` variable globale.

## <a name="see-also"></a>Voir aussi

[Prise en charge pour Unicode](../text/support-for-unicode.md)<br/>
[Résumé de la programmation Unicode](../text/unicode-programming-summary.md)<br/>
[Fonction WinMain](/windows/win32/api/winbase/nf-winbase-winmain)
