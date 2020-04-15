---
title: 'Procédure pas à pas : Créez une application Windows Desktop traditionnelle (C)'
description: Comment créer une application Windows Desktop minimale et traditionnelle à l’aide de Visual Studio, CMD et de l’API Win32
ms.custom: get-started-article
ms.date: 11/03/2019
helpviewer_keywords:
- Windows applications [C++], Win32
- Windows Desktop applications [C++]
- Windows API [C++]
ms.openlocfilehash: da74778e79a08dd3ed2b5be0675981425264bdc0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351850"
---
# <a name="walkthrough-create-a-traditional-windows-desktop-application-c"></a>Procédure pas à pas : Créez une application Windows Desktop traditionnelle (C)

Ce pas-là montre comment créer une application de bureau Windows traditionnelle dans Visual Studio. L’exemple que vous allez créer utilise l’API Windows pour afficher "Bonjour, bureau Windows!" dans une fenêtre. Vous pouvez utiliser le code que vous développez dans cette procédure pas à pas comme modèle pour créer d’autres applications de bureau Windows.

L’API Windows (également connue sous le nom d’API Win32, Windows Desktop API et Windows Classic API) est un cadre basé sur la langue C pour la création d’applications Windows. Il existe depuis les années 1980 et a été utilisé pour créer des applications Windows depuis des décennies. Des cadres plus avancés et plus faciles à programmer ont été construits au-dessus de l’API Windows. Par exemple, MFC, ATL, les cadres .NET. Même le code Windows Runtime le plus moderne pour les applications UWP et Store écrit dans C '/WinRT utilise l’API Windows en dessous. Pour plus d’informations sur l’API Windows, voir [Windows API Index](/windows/win32/apiindex/windows-api-list). Il existe de nombreuses façons de créer des applications Windows, mais le processus ci-dessus a été le premier.

> [!IMPORTANT]
> Par souci de brièveté, certaines déclarations de code sont omises dans le texte. La section [Construire le code](#build-the-code) à la fin de ce document affiche le code complet.

## <a name="prerequisites"></a>Prérequis

- Un ordinateur qui exécute Microsoft Windows 7 ou versions ultérieures. Nous recommandons Windows 10 pour une expérience de développement optimale.

- Une copie de Visual Studio. Pour plus d’informations sur le téléchargement et l’installation de Visual Studio, consultez [Installer Visual Studio](/visualstudio/install/install-visual-studio). Lorsque vous exécutez le programme d’installation, assurez-vous que la charge de travail **développement Desktop en C++** est activée. Ne vous inquiétez pas si vous n’avez pas installé cette charge de travail en même temps que Visual Studio. Vous pouvez réexécuter le programme d’installation et l’installer maintenant.

   ![Développement Desktop en C++](../build/media/desktop-development-with-cpp.png "Développement Desktop en C++")

- Une compréhension des principes fondamentaux de l’utilisation de l’IDE Visual Studio. Si vous avez déjà utilisé des applications de bureau Windows, vous n’aurez probablement aucun mal à suivre. Pour une introduction, consultez [Visite guidée des fonctionnalités de l’IDE Visual Studio](/visualstudio/ide/visual-studio-ide).

- Une compréhension de suffisamment de notions de base du langage C++ pour pouvoir suivre. Ne vous inquiétez pas, nous ne faisons rien de bien compliqué.

## <a name="create-a-windows-desktop-project"></a>Créer un projet de bureau Windows

Suivez ces étapes pour créer votre premier projet de bureau Windows. Au fur et à mesure, vous entrerez le code d’une application de bureau Windows fonctionnant. Pour voir la documentation de votre version préférée de Visual Studio, utilisez le contrôle du sélecteur **Version.** On le trouve en haut de la table des contenus sur cette page.

::: moniker range="vs-2019"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2019"></a>Créer un projet de bureau Windows dans Visual Studio 2019

1. Dans le menu principal, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Créer un projet**.

1. En haut du dialogue, définissez **la langue** en **C,** définissez **la plate-forme** vers **Windows,** et définissez **le type de projet** sur **Desktop**.

1. De la liste filtrée des types de projet, choisissez **Windows Desktop Wizard** puis choisissez **Next**. Dans la page suivante, entrez un nom pour le projet, par exemple, *DesktopApp*.

1. Choisissez le bouton **Créer** pour créer le projet.

1. Le dialogue **windows Desktop Project** apparaît maintenant. Sous **type d’application**, sélectionnez **l’application Desktop (.exe)**. Sous **Options supplémentaires**, sélectionnez **Projet vide**. Choisissez **OK** pour créer le projet.

1. Dans **Solution Explorer**, cliquez à droite sur le projet **DesktopApp,** choisissez **Ajouter,** puis choisissez **un nouvel article**.

   ![Ajouter un nouvel élément au projet DesktopApp](../build/media/desktop-app-project-add-new-item-153.gif "Ajouter un nouvel élément au projet DesktopApp")

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Fichier C++ (.cpp)**. Dans la boîte **nom,** tapez un nom pour le fichier, par exemple, *HelloWindowsDesktop.cpp*. Choisissez **Ajouter**.

   ![Ajouter le fichier .cpp au projet DesktopApp](../build/media/desktop-app-add-cpp-file-153.png "Ajouter le fichier .cpp au projet DesktopApp")

Votre projet est maintenant créé et votre fichier source est ouvert dans l’éditeur. Pour continuer, sautez à l’avance pour [créer le code](#create-the-code).

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2017"></a>Créer un projet de bureau Windows dans Visual Studio 2017

1. Dans le menu **Fichier**, choisissez **Nouveau**, puis **Projet**.

1. Dans la boîte de dialogue **new Project,** dans la vitre gauche, étendre Le visuel **installé,** > **Visual C++** puis sélectionnez **Windows Desktop**. Dans le volet du milieu, sélectionnez **Windows Desktop Wizard**.

   Dans la boîte **nom,** tapez un nom pour le projet, par exemple, *DesktopApp*. Choisissez **OK**.

   ![Nommez le projet DesktopApp](../build/media/desktop-app-new-project-name-153.png "Nommez le projet DesktopApp")

1. Dans le dialogue **Windows Desktop Project,** sous **type d’application**, sélectionnez **l’application Windows (.exe)**. Sous **Options supplémentaires**, sélectionnez **Projet vide**. Assurez-vous que **Precompiled Header** n’est pas sélectionné. Choisissez **OK** pour créer le projet.

1. Dans **Solution Explorer**, cliquez à droite sur le projet **DesktopApp,** choisissez **Ajouter,** puis choisissez **un nouvel article**.

   ![Ajouter un nouvel élément au projet DesktopApp](../build/media/desktop-app-project-add-new-item-153.gif "Ajouter un nouvel élément au projet DesktopApp")

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Fichier C++ (.cpp)**. Dans la boîte **nom,** tapez un nom pour le fichier, par exemple, *HelloWindowsDesktop.cpp*. Choisissez **Ajouter**.

   ![Ajouter le fichier .cpp au projet DesktopApp](../build/media/desktop-app-add-cpp-file-153.png "Ajouter le fichier .cpp au projet DesktopApp")

Votre projet est maintenant créé et votre fichier source est ouvert dans l’éditeur. Pour continuer, sautez à l’avance pour [créer le code](#create-the-code).

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2015"></a>Créer un projet de bureau Windows dans Visual Studio 2015

1. Dans le menu **Fichier**, choisissez **Nouveau**, puis **Projet**.

1. Dans la boîte de dialogue **du nouveau projet,** dans la vitre gauche, étendre les**modèles** >  **installés** > **Visual CMD**, puis sélectionnez **Win32**. Dans le volet central, sélectionnez **Projet Win32**.

   Dans la boîte **nom,** tapez un nom pour le projet, par exemple, *DesktopApp*. Choisissez **OK**.

   ![Nommez le projet DesktopApp](../build/media/desktop-app-new-project-name-150.png "Nommez le projet DesktopApp")

1. Sur la page **d’aperçu** de **l’assistant d’application Win32**, choisissez **Next**.

   ![Créez DesktopApp dans Win32 Application Wizard Overview](../build/media/desktop-app-win32-wizard-overview-150.png "Créez DesktopApp dans Win32 Application Wizard Overview")

1. Sur la page **Paramètres d’application,** sous **type d’application,** sélectionnez **l’application Windows**. En vertu **d’options supplémentaires**, uncheck **Precompiled header**, puis sélectionnez **projet vide**. Choisissez **Finition** pour créer le projet.

1. Dans **Solution Explorer**, cliquez à droite sur le projet DesktopApp, choisissez **Ajouter,** puis choisissez **un nouvel article**.

   ![Ajouter un nouvel élément au projet DesktopApp](../build/media/desktop-app-project-add-new-item-150.gif "Ajouter un nouvel élément au projet DesktopApp")

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Fichier C++ (.cpp)**. Dans la boîte **nom,** tapez un nom pour le fichier, par exemple, *HelloWindowsDesktop.cpp*. Choisissez **Ajouter**.

   ![Ajouter le fichier .cpp au projet DesktopApp](../build/media/desktop-app-add-cpp-file-150.png "Ajouter le fichier .cpp au projet DesktopApp")

Votre projet est maintenant créé et votre fichier source est ouvert dans l’éditeur.

::: moniker-end

## <a name="create-the-code"></a>Créer le code

Ensuite, vous apprendrez à créer le code d’une application de bureau Windows dans Visual Studio.

### <a name="to-start-a-windows-desktop-application"></a>Pour démarrer une application de bureau Windows

1. Tout comme chaque application C et application `main` CMD doit avoir une fonction comme `WinMain` point de départ, chaque application de bureau Windows doit avoir une fonction. La syntaxe de`WinMain` est la suivante.

   ```cpp
   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_opt_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   );
   ```

   Pour plus d’informations sur les paramètres et la valeur de retour de cette fonction, voir [le point d’entrée WinMain](/windows/win32/api/winbase/nf-winbase-winmain).

   > [!NOTE]
   > Quels sont tous ces mots `CALLBACK`supplémentaires, tels que , ou `HINSTANCE`, ou? `_In_` L’API Windows traditionnelle utilise des modules dactylographiés et des macros de préprocesseur en profondeur pour abstraction de certains détails des types et du code spécifique à la plate-forme, tels que les conventions d’appel, les déclarations **__declspec** et les pragmas compilateur. Dans Visual Studio, vous pouvez utiliser la fonction Info [rapide](/visualstudio/ide/using-intellisense#quick-info) IntelliSense pour voir ce que ces types et macros définissent. Planer votre souris sur le mot d’intérêt, ou sélectionnez-la et appuyez sur **Ctrl**+**K**, **Ctrl**+**I** pour une petite fenêtre pop-up qui contient la définition. Pour plus d’informations, consultez [Utilisation d’IntelliSense](/visualstudio/ide/using-intellisense). Les paramètres et les types de retour utilisent souvent *les annotations SAL* pour vous aider à saisir les erreurs de programmation. Pour plus d’informations, voir [Utiliser des annotations SAL pour réduire les défauts de code C/C .](/cpp/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects)

1. Les programmes &lt;de bureau Windows nécessitent des> windows.h. &lt;tchar.h> définit la `TCHAR` macro, qui décide en fin de compte de **wchar_t** si le symbole UNICODE est défini dans votre projet, sinon il se décide à **char**.  Si vous construisez toujours avec UNICODE activé, vous n’avez pas besoin de TCHAR et pouvez simplement utiliser **wchar_t** directement.

   ```cpp
   #include <windows.h>
   #include <tchar.h>
   ```

1. Avec la `WinMain` fonction, chaque application de bureau Windows doit également avoir une fonction de fenêtre-procédure. Cette fonction est `WndProc`généralement nommée, mais vous pouvez l’appeler ce que vous voulez. La syntaxe de`WndProc` est la suivante.

   ```cpp
   LRESULT CALLBACK WndProc(
      _In_ HWND   hWnd,
      _In_ UINT   message,
      _In_ WPARAM wParam,
      _In_ LPARAM lParam
   );
   ```

   Dans cette fonction, vous écrivez du code pour traiter les *messages* que l’application reçoit de Windows lorsque *des événements* se produisent. Par exemple, si un utilisateur choisit un bouton OK dans votre application, Windows vous `WndProc` enverra un message et vous pouvez écrire du code à l’intérieur de votre fonction qui fait tout le travail approprié. C’est ce qu’on appelle *la gestion* d’un événement. Vous ne gérez que les événements pertinents pour votre application.

   Pour plus d’informations, consultez [Window Procedures](/windows/win32/winmsg/window-procedures).

### <a name="to-add-functionality-to-the-winmain-function"></a>Pour ajouter une fonctionnalité à la fonction WinMain

1. Dans `WinMain` la fonction, vous remplissez une structure de type [WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw). La structure contient des informations sur la fenêtre: l’icône d’application, la couleur de fond de la fenêtre, le nom à afficher dans la barre de titre, entre autres choses. Fait important, il contient un pointeur de fonction à votre procédure de fenêtre. L’exemple suivant montre une structure `WNDCLASSEX` type.

   ```cpp
   WNDCLASSEX wcex;

   wcex.cbSize         = sizeof(WNDCLASSEX);
   wcex.style          = CS_HREDRAW | CS_VREDRAW;
   wcex.lpfnWndProc    = WndProc;
   wcex.cbClsExtra     = 0;
   wcex.cbWndExtra     = 0;
   wcex.hInstance      = hInstance;
   wcex.hIcon          = LoadIcon(hInstance, IDI_APPLICATION);
   wcex.hCursor        = LoadCursor(NULL, IDC_ARROW);
   wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1);
   wcex.lpszMenuName   = NULL;
   wcex.lpszClassName  = szWindowClass;
   wcex.hIconSm        = LoadIcon(wcex.hInstance, IDI_APPLICATION);
   ```

   Pour plus d’informations sur les champs de la structure ci-dessus, voir [WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw).

1. Enregistrez-le `WNDCLASSEX` avec Windows afin qu’il sache sur votre fenêtre et comment lui envoyer des messages. Utilisez la fonction [RegisterClassEx](/windows/win32/api/winuser/nf-winuser-registerclassexw) et passez la structure de classe de fenêtre comme argument. La `_T` macro est utilisée `TCHAR` parce que nous utilisons le type.

   ```cpp
   if (!RegisterClassEx(&wcex))
   {
      MessageBox(NULL,
         _T("Call to RegisterClassEx failed!"),
         _T("Windows Desktop Guided Tour"),
         NULL);

      return 1;
   }
   ```

1. Vous pouvez maintenant créer une fenêtre. Utilisez la fonction [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) .

   ```cpp
   static TCHAR szWindowClass[] = _T("DesktopApp");
   static TCHAR szTitle[] = _T("Windows Desktop Guided Tour Application");

   // The parameters to CreateWindow explained:
   // szWindowClass: the name of the application
   // szTitle: the text that appears in the title bar
   // WS_OVERLAPPEDWINDOW: the type of window to create
   // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y)
   // 500, 100: initial size (width, length)
   // NULL: the parent of this window
   // NULL: this application does not have a menu bar
   // hInstance: the first parameter from WinMain
   // NULL: not used in this application
   HWND hWnd = CreateWindow(
      szWindowClass,
      szTitle,
      WS_OVERLAPPEDWINDOW,
      CW_USEDEFAULT, CW_USEDEFAULT,
      500, 100,
      NULL,
      NULL,
      hInstance,
      NULL
   );
   if (!hWnd)
   {
      MessageBox(NULL,
         _T("Call to CreateWindow failed!"),
         _T("Windows Desktop Guided Tour"),
         NULL);

      return 1;
   }
   ```

   Cette fonction `HWND`renvoie un , qui est une poignée à une fenêtre. Une poignée est un peu comme un pointeur que Windows utilise pour garder une trace des fenêtres ouvertes. Pour plus d'informations, consultez [Types de données Windows](/windows/win32/WinProg/windows-data-types).

1. À ce stade, la fenêtre a été créée, mais nous avons encore besoin de dire à Windows pour le rendre visible. C’est ce que fait ce code :

   ```cpp
   // The parameters to ShowWindow explained:
   // hWnd: the value returned from CreateWindow
   // nCmdShow: the fourth parameter from WinMain
   ShowWindow(hWnd,
      nCmdShow);
   UpdateWindow(hWnd);
   ```

   La fenêtre affichée n’a pas beaucoup de contenu `WndProc` parce que vous n’avez pas encore implémenté la fonction. En d’autres termes, l’application ne gère pas encore les messages que Windows lui envoie maintenant.

1. Pour gérer les messages, nous ajoutons d’abord une boucle de message pour écouter les messages que Windows envoie. Lorsque l’application reçoit un message, cette `WndProc` boucle l’envoie à votre fonction pour être manipulé. La boucle de message ressemble au code suivant.

   ```cpp
   MSG msg;
   while (GetMessage(&msg, NULL, 0, 0))
   {
      TranslateMessage(&msg);
      DispatchMessage(&msg);
   }

   return (int) msg.wParam;
   ```

   Pour plus d’informations sur les structures et les fonctions dans la boucle de message, consultez [MSG](/windows/win32/api/winuser/ns-winuser-msg), [GetMessage](/windows/win32/api/winuser/nf-winuser-getmessage), [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)et [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).

   À ce stade, la fonction `WinMain` doit ressembler au code suivant.

   ```cpp
   int WINAPI WinMain(HINSTANCE hInstance,
                      HINSTANCE hPrevInstance,
                      LPSTR lpCmdLine,
                      int nCmdShow)
   {
      WNDCLASSEX wcex;

      wcex.cbSize = sizeof(WNDCLASSEX);
      wcex.style          = CS_HREDRAW | CS_VREDRAW;
      wcex.lpfnWndProc    = WndProc;
      wcex.cbClsExtra     = 0;
      wcex.cbWndExtra     = 0;
      wcex.hInstance      = hInstance;
      wcex.hIcon          = LoadIcon(hInstance, IDI_APPLICATION);
      wcex.hCursor        = LoadCursor(NULL, IDC_ARROW);
      wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1);
      wcex.lpszMenuName   = NULL;
      wcex.lpszClassName  = szWindowClass;
      wcex.hIconSm        = LoadIcon(wcex.hInstance, IDI_APPLICATION);

      if (!RegisterClassEx(&wcex))
      {
         MessageBox(NULL,
            _T("Call to RegisterClassEx failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // Store instance handle in our global variable
      hInst = hInstance;

      // The parameters to CreateWindow explained:
      // szWindowClass: the name of the application
      // szTitle: the text that appears in the title bar
      // WS_OVERLAPPEDWINDOW: the type of window to create
      // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y)
      // 500, 100: initial size (width, length)
      // NULL: the parent of this window
      // NULL: this application dows not have a menu bar
      // hInstance: the first parameter from WinMain
      // NULL: not used in this application
      HWND hWnd = CreateWindow(
         szWindowClass,
         szTitle,
         WS_OVERLAPPEDWINDOW,
         CW_USEDEFAULT, CW_USEDEFAULT,
         500, 100,
         NULL,
         NULL,
         hInstance,
         NULL
      );

      if (!hWnd)
      {
         MessageBox(NULL,
            _T("Call to CreateWindow failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // The parameters to ShowWindow explained:
      // hWnd: the value returned from CreateWindow
      // nCmdShow: the fourth parameter from WinMain
      ShowWindow(hWnd,
         nCmdShow);
      UpdateWindow(hWnd);

      // Main message loop:
      MSG msg;
      while (GetMessage(&msg, NULL, 0, 0))
      {
         TranslateMessage(&msg);
         DispatchMessage(&msg);
      }

      return (int) msg.wParam;
   }
   ```

### <a name="to-add-functionality-to-the-wndproc-function"></a>Pour ajouter une fonctionnalité à la fonction WndProc

1. Pour permettre à la fonction `WndProc` de traiter les messages reçus par l’application, implémentez une instruction switch.

   Un message important à gérer est le [message WM_PAINT.](/windows/win32/gdi/wm-paint) L’application `WM_PAINT` reçoit le message lorsqu’une partie de sa fenêtre affichée doit être mise à jour. L’événement peut se produire quand un utilisateur déplace une fenêtre en face de votre fenêtre, puis le déplace loin à nouveau. Votre application ne sait pas quand ces événements se produisent. Seul Windows le sait, il informe `WM_PAINT` votre application avec un message. Lorsque la fenêtre est affichée pour la première fois, tout cela doit être mis à jour.

   Pour traiter un message `WM_PAINT` , appelez d’abord [BeginPaint](/windows/win32/api/winuser/nf-winuser-beginpaint), puis traitez toute la logique pour disposer le texte, les boutons et autres contrôles dans la fenêtre, puis appelez [EndPaint](/windows/win32/api/winuser/nf-winuser-endpaint). Pour l’application, la logique entre l’appel de début et l’appel de fin est d’afficher la chaîne "Bonjour, bureau Windows!" dans la fenêtre. Dans le code suivant, notez que la fonction [TextOut](/windows/win32/api/wingdi/nf-wingdi-textoutw) est utilisée pour afficher la chaîne.

   ```cpp
   PAINTSTRUCT ps;
   HDC hdc;
   TCHAR greeting[] = _T("Hello, Windows desktop!");

   switch (message)
   {
   case WM_PAINT:
      hdc = BeginPaint(hWnd, &ps);

      // Here your application is laid out.
      // For this introduction, we just print out "Hello, Windows desktop!"
      // in the top left corner.
      TextOut(hdc,
         5, 5,
         greeting, _tcslen(greeting));
      // End application-specific layout section.

      EndPaint(hWnd, &ps);
      break;
   }
   ```

   `HDC`dans le code est une poignée à un contexte d’appareil, qui est une structure de données que Windows utilise pour permettre à votre application de communiquer avec le sous-système graphique. L’application `BeginPaint` et `EndPaint` les fonctions font que votre application se comporte comme un bon citoyen et n’utilise pas le contexte de l’appareil plus longtemps qu’il n’en a besoin. Les fonctions aident à rendre le sous-système graphique est disponible pour une utilisation par d’autres applications.

1. Une application gère généralement de nombreux autres messages. Par exemple, [WM_CREATE](/windows/win32/winmsg/wm-create) lorsqu’une fenêtre est créée et [WM_DESTROY](/windows/win32/winmsg/wm-destroy) lorsque la fenêtre est fermée. Le code suivant illustre une fonction `WndProc` basique mais complète.

   ```cpp
   LRESULT CALLBACK WndProc(HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam)
   {
      PAINTSTRUCT ps;
      HDC hdc;
      TCHAR greeting[] = _T("Hello, Windows desktop!");

      switch (message)
      {
      case WM_PAINT:
         hdc = BeginPaint(hWnd, &ps);

         // Here your application is laid out.
         // For this introduction, we just print out "Hello, Windows desktop!"
         // in the top left corner.
         TextOut(hdc,
            5, 5,
            greeting, _tcslen(greeting));
         // End application specific layout section.

         EndPaint(hWnd, &ps);
         break;
      case WM_DESTROY:
         PostQuitMessage(0);
         break;
      default:
         return DefWindowProc(hWnd, message, wParam, lParam);
         break;
      }

      return 0;
   }
   ```

## <a name="build-the-code"></a>Générer le code

Comme promis, voici le code complet pour l’application de travail.

### <a name="to-build-this-example"></a>Pour générer cet exemple

1. Supprimez tout code que vous avez entré dans *HelloWindowsDesktop.cpp* dans l’éditeur. Copiez ce code d’exemple et puis collez-le dans *HelloWindowsDesktop.cpp*:

   ```cpp
   // HelloWindowsDesktop.cpp
   // compile with: /D_UNICODE /DUNICODE /DWIN32 /D_WINDOWS /c

   #include <windows.h>
   #include <stdlib.h>
   #include <string.h>
   #include <tchar.h>

   // Global variables

   // The main window class name.
   static TCHAR szWindowClass[] = _T("DesktopApp");

   // The string that appears in the application's title bar.
   static TCHAR szTitle[] = _T("Windows Desktop Guided Tour Application");

   HINSTANCE hInst;

   // Forward declarations of functions included in this code module:
   LRESULT CALLBACK WndProc(HWND, UINT, WPARAM, LPARAM);

   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_opt_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   )
   {
      WNDCLASSEX wcex;

      wcex.cbSize = sizeof(WNDCLASSEX);
      wcex.style          = CS_HREDRAW | CS_VREDRAW;
      wcex.lpfnWndProc    = WndProc;
      wcex.cbClsExtra     = 0;
      wcex.cbWndExtra     = 0;
      wcex.hInstance      = hInstance;
      wcex.hIcon          = LoadIcon(hInstance, IDI_APPLICATION);
      wcex.hCursor        = LoadCursor(NULL, IDC_ARROW);
      wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1);
      wcex.lpszMenuName   = NULL;
      wcex.lpszClassName  = szWindowClass;
      wcex.hIconSm        = LoadIcon(wcex.hInstance, IDI_APPLICATION);

      if (!RegisterClassEx(&wcex))
      {
         MessageBox(NULL,
            _T("Call to RegisterClassEx failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // Store instance handle in our global variable
      hInst = hInstance;

      // The parameters to CreateWindow explained:
      // szWindowClass: the name of the application
      // szTitle: the text that appears in the title bar
      // WS_OVERLAPPEDWINDOW: the type of window to create
      // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y)
      // 500, 100: initial size (width, length)
      // NULL: the parent of this window
      // NULL: this application does not have a menu bar
      // hInstance: the first parameter from WinMain
      // NULL: not used in this application
      HWND hWnd = CreateWindow(
         szWindowClass,
         szTitle,
         WS_OVERLAPPEDWINDOW,
         CW_USEDEFAULT, CW_USEDEFAULT,
         500, 100,
         NULL,
         NULL,
         hInstance,
         NULL
      );

      if (!hWnd)
      {
         MessageBox(NULL,
            _T("Call to CreateWindow failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // The parameters to ShowWindow explained:
      // hWnd: the value returned from CreateWindow
      // nCmdShow: the fourth parameter from WinMain
      ShowWindow(hWnd,
         nCmdShow);
      UpdateWindow(hWnd);

      // Main message loop:
      MSG msg;
      while (GetMessage(&msg, NULL, 0, 0))
      {
         TranslateMessage(&msg);
         DispatchMessage(&msg);
      }

      return (int) msg.wParam;
   }

   //  FUNCTION: WndProc(HWND, UINT, WPARAM, LPARAM)
   //
   //  PURPOSE:  Processes messages for the main window.
   //
   //  WM_PAINT    - Paint the main window
   //  WM_DESTROY  - post a quit message and return
   LRESULT CALLBACK WndProc(HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam)
   {
      PAINTSTRUCT ps;
      HDC hdc;
      TCHAR greeting[] = _T("Hello, Windows desktop!");

      switch (message)
      {
      case WM_PAINT:
         hdc = BeginPaint(hWnd, &ps);

         // Here your application is laid out.
         // For this introduction, we just print out "Hello, Windows desktop!"
         // in the top left corner.
         TextOut(hdc,
            5, 5,
            greeting, _tcslen(greeting));
         // End application-specific layout section.

         EndPaint(hWnd, &ps);
         break;
      case WM_DESTROY:
         PostQuitMessage(0);
         break;
      default:
         return DefWindowProc(hWnd, message, wParam, lParam);
         break;
      }

      return 0;
   }
   ```

1. Dans le menu **Générer** , choisissez **Générer la solution**. Les résultats de la compilation doivent apparaître dans la fenêtre **Output** dans Visual Studio.

   ![Construire le projet DesktopApp](../build/media/desktop-app-project-build-150.gif "Construire le projet DesktopApp")

1. Pour exécuter l'application, appuyez sur **F5**. Une fenêtre qui contient le texte "Bonjour, bureau Windows!" doit apparaître dans le coin supérieur gauche de l’affichage.

   ![Exécuter le projet DesktopApp](../build/media/desktop-app-project-run-157.PNG "Exécuter le projet DesktopApp")

Félicitations ! Vous avez terminé cette procédure pas à pas et construit une application de bureau Windows traditionnelle.

## <a name="see-also"></a>Voir aussi

[Windows Desktop Applications](../windows/windows-desktop-applications-cpp.md)
