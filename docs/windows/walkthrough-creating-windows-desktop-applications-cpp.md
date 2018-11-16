---
title: 'Procédure pas à pas : Créer une application de bureau de Windows traditionnelle (C++)'
ms.custom: get-started-article
ms.date: 09/18/2018
helpviewer_keywords:
- Windows applications [C++], Win32
- Windows Desktop applications [C++]
- Windows API [C++]
ms.openlocfilehash: da95b1dac2f058de67719b4754d2df6dbeb6f7f0
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694047"
---
# <a name="walkthrough-create-a-traditional-windows-desktop-application-c"></a>Procédure pas à pas : Créer une application de bureau de Windows traditionnelle (C++)

Cette procédure pas à pas montre comment créer une application de bureau Windows classique dans Visual Studio. L’exemple d’application, vous allez créer utilise l’API Windows pour afficher « Hello, bureau de Windows ! » dans une fenêtre. Vous pouvez utiliser le code que vous développez dans cette procédure pas à pas comme modèle pour créer d’autres applications de bureau Windows.

L’API Windows (également appelé l’API Win32, API de bureau Windows et API classique de Windows) est une infrastructure basée sur la langue de C pour créer des applications Windows. Il a été existe depuis les années 1980 et a été utilisé pour créer des applications de Windows depuis des décennies. Plus les infrastructures avancées et plus facile à programme ont été construits par-dessus l’API Windows, telles que MFC, ATL et .NET Framework. Code les plus moderne pour les applications UWP et Store écrites en C / c++ / WinRT utilise l’API Windows en dessous. Pour plus d’informations sur l’API Windows, consultez [Index d’API Windows](/windows/desktop/apiindex/windows-api-list). Il existe plusieurs façons de créer des applications Windows, mais le processus ci-dessus a été le premier.

> [!IMPORTANT]
> Par souci de concision, certaines instructions de code sont omises dans le texte. Le [générer le code](#build-the-code) section à la fin de ce document présente le code complet.

## <a name="prerequisites"></a>Prérequis

- Un ordinateur qui exécute Microsoft Windows 7 ou versions ultérieures. Nous recommandons Windows 10 pour la meilleure expérience de développement.

- Une copie de Visual Studio 2017. Pour plus d’informations sur la façon de télécharger et installer Visual Studio, consultez [installer Visual Studio](/visualstudio/install/install-visual-studio). Lorsque vous exécutez le programme d’installation, assurez-vous que le **développement Desktop en C++** charge de travail est activée. Ne vous inquiétez pas si vous n’avez pas installé cette charge de travail lorsque vous avez installé Visual Studio. Vous pouvez réexécuter le programme d’installation et l’installer maintenant.

   ![Développement Desktop en C++](../build/media/desktop-development-with-cpp.png "développement Desktop en C++")

- Une compréhension des principes fondamentaux de l’utilisation de l’IDE Visual Studio. Si vous avez utilisé des applications de bureau Windows avant, vous pouvez probablement vous tenir. Pour une introduction, consultez [visite guidée des fonctionnalités IDE de Visual Studio](/visualstudio/ide/visual-studio-ide).

- Comprendre suffisamment les principes fondamentaux du langage C++ pour suivre la procédure. Ne vous inquiétez pas, nous ne font rien trop compliqué.

## <a name="create-a-windows-desktop-project"></a>Créez un projet de bureau Windows

Suivez ces étapes pour créer votre premier projet de bureau Windows et entrez le code pour une application de bureau Windows de travail. Si vous utilisez une version de Visual Studio antérieures à Visual Studio 2017 version 15.3, passez directement à [pour créer un projet de bureau Windows dans Visual Studio 2017 RTM](#create-in-vs2017-rtm).

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2017-update-153-and-later"></a>Pour créer un projet de bureau Windows dans Visual Studio 2017 mise à jour 15.3 et versions ultérieures

1. Dans le menu **Fichier**, choisissez **Nouveau**, puis **Projet**.

1. Dans le **nouveau projet** boîte de dialogue, dans le volet gauche, développez **installé** > **Visual C++**, puis sélectionnez **Windows Desktop**. Dans le volet central, sélectionnez **Windows Desktop Assistant**.

   Dans le **nom** , tapez un nom pour le projet, par exemple, *DesktopApp*. Cliquez sur **OK**.

   ![Nommez le projet DesktopApp](../build/media/desktop-app-new-project-name-153.png "nommez le projet DesktopApp")

1. Dans le **projet de bureau Windows** boîte de dialogue, sous **type d’Application**, sélectionnez **application Windows (.exe)**. Sous **Options supplémentaires**, sélectionnez **Projet vide**. Choisissez **OK** pour créer le projet.

   ![Créer DesktopApp dans l’Assistant de projet de bureau Windows](../build/media/desktop-app-new-project-wizard-153.png "créer DesktopApp dans l’Assistant de projet de bureau Windows")

1. Dans **l’Explorateur de solutions**, avec le bouton droit le **DesktopApp** de projet, choisissez **ajouter**, puis choisissez **un nouvel élément**.

   ![Ajouter un nouvel élément au projet de DesktopApp](../build/media/desktop-app-project-add-new-item-153.gif "ajouter un nouvel élément au projet de DesktopApp")

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Fichier C++ (.cpp)**. Dans le **nom** , tapez un nom pour le fichier, par exemple, *HelloWindowsDesktop.cpp*. Sélectionnez **Ajouter**.

   ![Ajouter un fichier .cpp au projet de DesktopApp](../build/media/desktop-app-add-cpp-file-153.png "ajouter un fichier .cpp à DesktopApp projet")

Votre projet est maintenant créé et votre fichier source s’ouvre dans l’éditeur. Pour continuer, passez directement à [créer le code](#create-the-code).

### <a id="create-in-vs2017-rtm"></a> Pour créer un projet de bureau Windows dans Visual Studio 2017 RTM

1. Dans le menu **Fichier**, choisissez **Nouveau**, puis **Projet**.

1. Dans le **nouveau projet** boîte de dialogue, dans le volet gauche, développez **installé** > **modèles** > **Visual C++**, puis sélectionnez **Win32**. Dans le volet central, sélectionnez **Projet Win32**.

   Dans le **nom** , tapez un nom pour le projet, par exemple, *DesktopApp*. Cliquez sur **OK**.

   ![Nommez le projet DesktopApp](../build/media/desktop-app-new-project-name-150.png "nommez le projet DesktopApp")

1. Sur le **vue d’ensemble** page de la **Assistant Application Win32**, choisissez **suivant**.

   ![Créer DesktopApp dans Présentation de l’Assistant Application Win32](../build/media/desktop-app-win32-wizard-overview-150.png "créer DesktopApp dans Présentation de l’Assistant Application Win32")

1. Sur le **paramètres d’Application** page sous **type d’Application**, sélectionnez **application du Windows**. Sous **Options supplémentaires**, sélectionnez **Projet vide**. Choisissez **Terminer** pour créer le projet.

   ![Créer DesktopApp dans les paramètres de l’Assistant Application Win32](../build/media/desktop-app-win32-wizard-settings-150.png "créer DesktopApp dans les paramètres de l’Assistant Application Win32")

1. Dans **l’Explorateur de solutions**, cliquez sur le projet DesktopApp, choisissez **ajouter**, puis choisissez **un nouvel élément**.

   ![Ajouter un nouvel élément au projet de DesktopApp](../build/media/desktop-app-project-add-new-item-150.gif "ajouter un nouvel élément au projet de DesktopApp")

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Fichier C++ (.cpp)**. Dans le **nom** , tapez un nom pour le fichier, par exemple, *HelloWindowsDesktop.cpp*. Sélectionnez **Ajouter**.

   ![Ajouter un fichier .cpp au projet de DesktopApp](../build/media/desktop-app-add-cpp-file-150.png "ajouter un fichier .cpp à DesktopApp projet")

Votre projet est maintenant créé et votre fichier source s’ouvre dans l’éditeur.

## <a name="create-the-code"></a>Créer le code

Ensuite, vous allez apprendre à créer le code d’une application de bureau Windows dans Visual Studio.

### <a name="to-start-a-windows-desktop-application"></a>Pour démarrer une application de bureau Windows

1. Tout comme chaque C application et l’application C++ doivent avoir un `main` fonctionner en tant que point de départ, chaque Windows application de bureau doit avoir un `WinMain` (fonction). La syntaxe de`WinMain` est la suivante.

   ```cpp
   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   );
   ```

   Pour plus d’informations sur les paramètres et la valeur de retour de cette fonction, consultez [point d’entrée WinMain](https://msdn.microsoft.com/library/windows/desktop/ms633559).

   > [!NOTE]
   > Quelles sont ces mots supplémentaires, telles que `CALLBACK`, ou `HINSTANCE`, ou `_In_`? L’API Windows traditionnelles utilise typedefs et macros de préprocesseur largement à clarifient certains détails des types et spécifique à la plateforme de code, telles que l’appel de conventions, **__declspec** déclarations et des pragmas du compilateur. Dans Visual Studio, vous pouvez utiliser IntelliSense [Info Express](/visualstudio/ide/using-intellisense#quick-info) fonctionnalité pour voir ce que définissent ces typedefs et les macros. Pointez votre souris sur le mot qui vous intéresse, ou sélectionnez-le et appuyez sur **Ctrl**+**K**, **Ctrl**+**je** pour un petite fenêtre contextuelle qui contient la définition. Pour plus d’informations, consultez [Utilisation d’IntelliSense](/visualstudio/ide/using-intellisense). Paramètres et types de retour utilisent souvent *Annotations SAL* pour vous aider à catch des erreurs de programmation. Pour plus d’informations, consultez [à l’aide d’Annotations SAL pour réduire les défauts du Code C/C++](/visualstudio/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects).

1. Programmes de bureau Windows nécessitent &lt;windows.h >. &lt;Tchar.h > définit le `TCHAR` (macro), qui se résout en fin de compte à **wchar_t** si le symbole UNICODE est défini dans votre projet, sinon elle est résolue à **char**.  Si vous générez toujours avec UNICODE est activé, vous ne devez TCHAR et peut utiliser tout simplement **wchar_t** directement.

   ```cpp
   #include <windows.h>
   #include <tchar.h>
   ```

1. Outre la fonction `WinMain` , chaque application de bureau Windows doit avoir une fonction de procédure de fenêtre. Cette fonction est généralement nommée `WndProc` , mais vous pouvez le nommer comme vous le souhaitez. La syntaxe de`WndProc` est la suivante.

   ```cpp
   LRESULT CALLBACK WndProc(
      _In_ HWND   hwnd,
      _In_ UINT   uMsg,
      _In_ WPARAM wParam,
      _In_ LPARAM lParam
   );
   ```

   Dans cette fonction, vous écrivez du code pour gérer les *messages* reçues par l’application à partir de Windows quand *événements* se produisent. Par exemple, si un utilisateur choisit un bouton OK dans votre application, Windows envoie un message à vous et vous pouvez écrire du code à l’intérieur de votre `WndProc` fonction qui effectue le travail approprié. Il est appelé *gestion* un événement. Vous gérez uniquement les événements qui sont pertinentes pour votre application.

   Pour plus d’informations, consultez [Window Procedures](/windows/desktop/winmsg/window-procedures).

### <a name="to-add-functionality-to-the-winmain-function"></a>Pour ajouter une fonctionnalité à la fonction WinMain

1. Dans le `WinMain` (fonction), vous remplissez une structure de type [WNDCLASSEX](https://msdn.microsoft.com/library/windows/desktop/ms633577). La structure contient des informations sur la fenêtre, par exemple, l’icône d’application, la couleur d’arrière-plan de la fenêtre, le nom à afficher dans la barre de titre et plus important encore, un pointeur de fonction à votre procédure de fenêtre. L’exemple suivant montre une structure `WNDCLASSEX` type.

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

   Pour plus d’informations sur les champs de la structure ci-dessus, consultez [WNDCLASSEX](https://msdn.microsoft.com/library/windows/desktop/ms633577).

1. Inscrire le `WNDCLASSEX` avec Windows afin qu’il connaît votre fenêtre et comment lui envoyer des messages. Utilisez la fonction [RegisterClassEx](/windows/desktop/api/winuser/nf-winuser-registerclassexa) et passez la structure de classe de fenêtre comme argument. Le `_T` macro est utilisée, car nous utilisons le `TCHAR` type.

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

1. Vous pouvez maintenant créer une fenêtre. Utilisez la fonction [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) .

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

   Cette fonction retourne un `HWND`, qui est un handle de fenêtre. Un handle est un peu comme un pointeur Windows utilise pour effectuer le suivi des fenêtres ouvertes. Pour plus d'informations, consultez [Types de données Windows](/windows/desktop/WinProg/windows-data-types).

1. À ce stade, la fenêtre a été créée, mais nous avons besoin indiquer à Windows pour le rendre visible. C’est ce que fait ce code :

   ```cpp
   // The parameters to ShowWindow explained:
   // hWnd: the value returned from CreateWindow
   // nCmdShow: the fourth parameter from WinMain
   ShowWindow(hWnd,
      nCmdShow);
   UpdateWindow(hWnd);
   ```

   Quantité de contenu n’a pas la fenêtre affichée, car vous n’avez pas encore implémenté le `WndProc` (fonction). En d’autres termes, l’application ne n’est pas encore gère les messages que Windows envoie désormais à celui-ci.

1. Pour gérer les messages, nous ajoutez tout d’abord une boucle de message pour écouter les messages envoyés par Windows. Lorsque l’application reçoit un message, cette boucle l’envoie à votre `WndProc` fonction à traiter. La boucle de message ressemble au code suivant.

   ```cpp
   MSG msg;
   while (GetMessage(&msg, NULL, 0, 0))
   {
      TranslateMessage(&msg);
      DispatchMessage(&msg);
   }

   return (int) msg.wParam;
   ```

   Pour plus d’informations sur les structures et les fonctions dans la boucle de message, consultez [MSG](https://msdn.microsoft.com/library/windows/desktop/ms644958), [GetMessage](/windows/desktop/api/winuser/nf-winuser-getmessage), [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage)et [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage).

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

   Est un message important pour gérer la [WM_PAINT](/windows/desktop/gdi/wm-paint) message. L’application reçoit le `WM_PAINT` message lorsqu’il fait partie de sa fenêtre affichée doit être mis à jour. L’événement peut se produire lorsqu’un utilisateur déplace une fenêtre devant votre fenêtre, puis le déplace à nouveau, et que votre application ne sait pas lorsque ces événements se produisent. Windows seulement sait, il vous avertit avec `WM_PAINT`. Lorsque la fenêtre s’affiche tout d’abord, tout cela doit être mis à jour.

   Pour traiter un message `WM_PAINT` , appelez d’abord [BeginPaint](/windows/desktop/api/winuser/nf-winuser-beginpaint), puis traitez toute la logique pour disposer le texte, les boutons et autres contrôles dans la fenêtre, puis appelez [EndPaint](/windows/desktop/api/winuser/nf-winuser-endpaint). Pour l’application, la logique entre l’appel de début et de l’appel de fin consiste à afficher la chaîne « Hello, bureau de Windows ! » dans la fenêtre. Dans le code suivant, notez que la fonction [TextOut](/windows/desktop/api/wingdi/nf-wingdi-textouta) est utilisée pour afficher la chaîne.

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

   `HDC` dans le code est un handle vers un contexte de périphérique, qui est une structure de données que Windows utilise pour permettre à votre application communiquer avec le sous-système graphique. Le `BeginPaint` et `EndPaint` fonctions que votre application se comporte comme un bon citoyen et n’utilise pas le contexte de périphérique pendant plus longtemps que nécessaire. Le fonctions contribuent à rendre le sous-système graphique est disponible pour une utilisation par d’autres applications.

1. Une application gère généralement beaucoup d’autres messages, par exemple, [WM_CREATE](/windows/desktop/winmsg/wm-create) lors de la création d’une fenêtre, et [WM_DESTROY](/windows/desktop/winmsg/wm-destroy) lorsque la fenêtre est fermée. Le code suivant illustre une fonction `WndProc` basique mais complète.

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

Comme annoncé, voici le code complet pour l’application fonctionnelle.

### <a name="to-build-this-example"></a>Pour générer cet exemple

1. Supprimez tout code que vous avez entré dans *HelloWindowsDesktop.cpp* dans l’éditeur. Copiez cet exemple de code et collez-le dans *HelloWindowsDesktop.cpp*:

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
      _In_ HINSTANCE hPrevInstance,
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

1. Dans le menu **Générer** , choisissez **Générer la solution**. Les résultats de la compilation doivent apparaître dans le **sortie** fenêtre dans Visual Studio.

   ![Générez le projet DesktopApp](../build/media/desktop-app-project-build-150.gif "générer le projet DesktopApp")

1. Pour exécuter l’application, appuyez sur **F5**. Une fenêtre qui contient le texte « Hello, bureau de Windows ! » doit apparaître dans le coin supérieur gauche de l’affichage.

   ![Exécutez le projet DesktopApp](../build/media/desktop-app-project-run-157.png "exécuter le projet DesktopApp")

Félicitations ! Vous avez terminé cette procédure pas à pas et créé une application de bureau Windows traditionnelle.

## <a name="see-also"></a>Voir aussi

[Applications de bureau Windows](../windows/windows-desktop-applications-cpp.md)