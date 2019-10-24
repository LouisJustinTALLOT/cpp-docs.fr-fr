---
title: 'Procédure pas à pas : création d’une applicationC++de bureau Windows traditionnelle ()'
ms.custom: get-started-article
ms.date: 10/21/2019
helpviewer_keywords:
- Windows applications [C++], Win32
- Windows Desktop applications [C++]
- Windows API [C++]
ms.openlocfilehash: 080c4cd9612058a0a54f19e5d0f4b8add4a03bce
ms.sourcegitcommit: ea9d78dbb93bf3f8841dde93dbc12bd66f6f32ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72778550"
---
# <a name="walkthrough-create-a-traditional-windows-desktop-application-c"></a>Procédure pas à pas : création d’une applicationC++de bureau Windows traditionnelle ()

Cette procédure pas à pas montre comment créer une application de bureau Windows traditionnelle dans Visual Studio. L’exemple d’application que vous allez créer utilise l’API Windows pour afficher « Hello, Windows Desktop ! » dans une fenêtre. Vous pouvez utiliser le code que vous développez dans cette procédure pas à pas comme modèle pour créer d’autres applications de bureau Windows.

L’API Windows (également appelée API Win32, Windows Desktop API et Windows API classique) est une infrastructure basée sur le langage C pour la création d’applications Windows. Il existe depuis les années 1980 et a été utilisé pour créer des applications Windows depuis des décennies. Des frameworks plus avancés et plus faciles à programmer ont été créés en plus de l’API Windows. Par exemple, MFC, ATL, .NET Framework. Même le code Windows Runtime le plus moderne pour les applications UWP et Store C++écrites dans/WinRT utilise l’API Windows ci-dessous. Pour plus d’informations sur l’API Windows, consultez index de l' [API Windows](/windows/win32/apiindex/windows-api-list). Il existe de nombreuses façons de créer des applications Windows, mais le processus ci-dessus a été le premier.

> [!IMPORTANT]
> Par souci de concision, certaines instructions de code sont omises dans le texte. La section [créer la](#build-the-code) section de code à la fin de ce document montre le code complet.

## <a name="prerequisites"></a>Configuration requise

- Un ordinateur qui exécute Microsoft Windows 7 ou versions ultérieures. Nous recommandons Windows 10 pour une expérience de développement optimale.

- Une copie de Visual Studio. Pour plus d’informations sur le téléchargement et l’installation de Visual Studio, consultez [Installer Visual Studio](/visualstudio/install/install-visual-studio). Lorsque vous exécutez le programme d’installation, assurez-vous que la charge de travail **développement Desktop en C++** est activée. Ne vous inquiétez pas si vous n’avez pas installé cette charge de travail en même temps que Visual Studio. Vous pouvez réexécuter le programme d’installation et l’installer maintenant.

   ![Développement Desktop avec C++](../build/media/desktop-development-with-cpp.png "Développement Desktop avec C++")

- Une compréhension des principes fondamentaux de l’utilisation de l’IDE Visual Studio. Si vous avez déjà utilisé des applications de bureau Windows, vous n’aurez probablement aucun mal à suivre. Pour une introduction, consultez [Visite guidée des fonctionnalités de l’IDE Visual Studio](/visualstudio/ide/visual-studio-ide).

- Une compréhension de suffisamment de notions de base du langage C++ pour pouvoir suivre. Ne vous inquiétez pas, nous ne faisons rien de bien compliqué.

## <a name="create-a-windows-desktop-project"></a>Créer un projet de bureau Windows

Procédez comme suit pour créer votre premier projet de bureau Windows. Au fur et à mesure, vous allez entrer le code d’une application de bureau Windows opérationnelle. Il y a un sélecteur de version dans l’angle supérieur gauche de cette page. Assurez-vous qu’il est défini sur la version de Visual Studio que vous utilisez.

::: moniker range="vs-2019"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2019"></a>Pour créer un projet de bureau Windows dans Visual Studio 2019

1. Dans le menu principal, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Créer un projet**.

1. En haut de la boîte de dialogue, définissez Language **C++** sur, Set **Platform** to **Windows**et Set **Project type** sur **Desktop**.

1. Dans la liste filtrée des types de projets, choisissez **Windows Desktop Wizard** , puis choisissez **suivant**. Dans la page suivante, entrez un nom pour le projet, par exemple, *DesktopApp*.

1. Choisissez le bouton **Créer** pour créer le projet.

1. La boîte de dialogue **projet de bureau Windows** s’affiche maintenant. Sous **type d’application**, sélectionnez **application de bureau (. exe)** . Sous **Options supplémentaires**, sélectionnez **Projet vide**. Choisissez **OK** pour créer le projet.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **DesktopApp** , choisissez **Ajouter**, puis **nouvel élément**.

   ![Ajouter un nouvel élément au projet DesktopApp](../build/media/desktop-app-project-add-new-item-153.gif "Ajouter un nouvel élément au projet DesktopApp")

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Fichier C++ (.cpp)** . Dans la zone **nom** , tapez un nom pour le fichier, par exemple, *HelloWindowsDesktop. cpp*. Sélectionnez **Ajouter**.

   ![Ajouter un fichier. cpp au projet DesktopApp](../build/media/desktop-app-add-cpp-file-153.png "Ajouter un fichier. cpp au projet DesktopApp")

Votre projet est maintenant créé et votre fichier source s’ouvre dans l’éditeur. Pour continuer, passez directement à [la création du code](#create-the-code).

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2017"></a>Pour créer un projet de bureau Windows dans Visual Studio 2017

1. Dans le menu **Fichier**, choisissez **Nouveau**, puis **Projet**.

1. Dans le volet gauche de la boîte de dialogue **nouveau projet** , développez **installé**  > **C++visuel**, puis sélectionnez **Bureau Windows**. Dans le volet central, sélectionnez **Windows Desktop Wizard**.

   Dans la zone **nom** , tapez un nom pour le projet, par exemple, *DesktopApp*. Cliquez sur **OK**.

   ![Nommer le projet DesktopApp](../build/media/desktop-app-new-project-name-153.png "Nommer le projet DesktopApp")

1. Dans la boîte de dialogue **projet de bureau Windows** , sous **type d’application**, sélectionnez **application Windows (. exe)** . Sous **Options supplémentaires**, sélectionnez **Projet vide**. Choisissez **OK** pour créer le projet.

   ![Assistant créer un DesktopApp dans un projet de bureau Windows](../build/media/desktop-app-new-project-wizard-153.png "Assistant créer un DesktopApp dans un projet de bureau Windows")

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **DesktopApp** , choisissez **Ajouter**, puis **nouvel élément**.

   ![Ajouter un nouvel élément au projet DesktopApp](../build/media/desktop-app-project-add-new-item-153.gif "Ajouter un nouvel élément au projet DesktopApp")

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Fichier C++ (.cpp)** . Dans la zone **nom** , tapez un nom pour le fichier, par exemple, *HelloWindowsDesktop. cpp*. Sélectionnez **Ajouter**.

   ![Ajouter un fichier. cpp au projet DesktopApp](../build/media/desktop-app-add-cpp-file-153.png "Ajouter un fichier. cpp au projet DesktopApp")

Votre projet est maintenant créé et votre fichier source s’ouvre dans l’éditeur. Pour continuer, passez directement à [la création du code](#create-the-code).

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2015"></a>Pour créer un projet de bureau Windows dans Visual Studio 2015

1. Dans le menu **Fichier**, choisissez **Nouveau**, puis **Projet**.

1. Dans le volet gauche de la boîte de dialogue **nouveau projet** , développez  > **modèles** **installés**  > **C++visuel**, puis sélectionnez **Win32**. Dans le volet central, sélectionnez **Projet Win32**.

   Dans la zone **nom** , tapez un nom pour le projet, par exemple, *DesktopApp*. Cliquez sur **OK**.

   ![Nommer le projet DesktopApp](../build/media/desktop-app-new-project-name-150.png "Nommer le projet DesktopApp")

1. Sur la page **vue d’ensemble** de l' **Assistant application Win32**, choisissez **suivant**.

   ![Vue d’ensemble de l’assistant créer un DesktopApp dans l’application Win32](../build/media/desktop-app-win32-wizard-overview-150.png "Vue d’ensemble de l’assistant créer un DesktopApp dans l’application Win32")

1. Sur la page Paramètres de l' **application** , sous **type d’application**, sélectionnez **application Windows**. Sous **Options supplémentaires**, sélectionnez **Projet vide**. Choisissez **Terminer** pour créer le projet.

   ![Paramètres de l’assistant créer un DesktopApp dans l’application Win32](../build/media/desktop-app-win32-wizard-settings-150.png "Paramètres de l’assistant créer un DesktopApp dans l’application Win32")

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet DesktopApp, choisissez **Ajouter**, puis **nouvel élément**.

   ![Ajouter un nouvel élément au projet DesktopApp](../build/media/desktop-app-project-add-new-item-150.gif "Ajouter un nouvel élément au projet DesktopApp")

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Fichier C++ (.cpp)** . Dans la zone **nom** , tapez un nom pour le fichier, par exemple, *HelloWindowsDesktop. cpp*. Sélectionnez **Ajouter**.

   ![Ajouter un fichier. cpp au projet DesktopApp](../build/media/desktop-app-add-cpp-file-150.png "Ajouter un fichier. cpp au projet DesktopApp")

Votre projet est maintenant créé et votre fichier source s’ouvre dans l’éditeur.

::: moniker-end

## <a name="create-the-code"></a>Créer le code

Ensuite, vous apprendrez à créer le code d’une application de bureau Windows dans Visual Studio.

### <a name="to-start-a-windows-desktop-application"></a>Pour démarrer une application de bureau Windows

1. Tout comme chaque application et C++ application C doit avoir une fonction de `main` comme point de départ, chaque application de bureau Windows doit avoir une fonction `WinMain`. La syntaxe de`WinMain` est la suivante.

   ```cpp
   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_opt_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   );
   ```

   Pour plus d’informations sur les paramètres et la valeur de retour de cette fonction, consultez [point d’entrée WinMain](/windows/win32/api/winbase/nf-winbase-winmain).

   > [!NOTE]
   > Quels sont les mots supplémentaires, tels que `CALLBACK` ou `HINSTANCE` ou `_In_` ? L’API Windows traditionnelle utilise les typedefs et les macros de préprocesseur pour résumer les détails des types et du code spécifique à la plateforme, comme les conventions d’appel, les déclarations **_ _ declspec** et les pragmas de compilateur. Dans Visual Studio, vous pouvez utiliser la fonctionnalité [Info Express](/visualstudio/ide/using-intellisense#quick-info) IntelliSense pour voir ce que les typedefs et les macros définissent. Pointez votre souris sur le mot qui vous intéresse, ou sélectionnez-le et appuyez sur **ctrl** +**K**, **CTRL** +**I** pour une petite fenêtre contextuelle contenant la définition. Pour plus d’informations, consultez [Utilisation d’IntelliSense](/visualstudio/ide/using-intellisense). Les paramètres et les types de retour utilisent souvent des *Annotations SAL* pour vous aider à intercepter les erreurs de programmation. Pour plus d’informations, consultez [utilisation d’annotations SAL pourC++ réduire les défauts C/code](/visualstudio/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects).

1. Les programmes de bureau Windows requièrent &lt;windows. h >. &lt;tchar. h > définit la macro `TCHAR`, qui correspond finalement à **wchar_t** si le symbole Unicode est défini dans votre projet, sinon elle est résolue en **char**.  Si vous générez toujours avec UNICODE activé, vous n’avez pas besoin de TCHAR et pouvez simplement utiliser **wchar_t** directement.

   ```cpp
   #include <windows.h>
   #include <tchar.h>
   ```

1. Avec la fonction `WinMain`, chaque application de bureau Windows doit également avoir une fonction de procédure de fenêtre. Cette fonction est généralement nommée `WndProc`, mais vous pouvez la nommer comme vous le souhaitez. La syntaxe de`WndProc` est la suivante.

   ```cpp
   LRESULT CALLBACK WndProc(
      _In_ HWND   hWnd,
      _In_ UINT   message,
      _In_ WPARAM wParam,
      _In_ LPARAM lParam
   );
   ```

   Dans cette fonction, vous écrivez du code pour gérer les *messages* que l’application reçoit de Windows lorsque des *événements* se produisent. Par exemple, si un utilisateur choisit un bouton OK dans votre application, Windows vous envoie un message et vous pouvez écrire du code à l’intérieur de votre fonction `WndProc` qui effectue tout ce qui est approprié. Elle est appelée *gérant* un événement. Vous gérez uniquement les événements pertinents pour votre application.

   Pour plus d’informations, consultez [Window Procedures](/windows/win32/winmsg/window-procedures).

### <a name="to-add-functionality-to-the-winmain-function"></a>Pour ajouter une fonctionnalité à la fonction WinMain

1. Dans la fonction `WinMain`, vous remplissez une structure de type [WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw). La structure contient des informations sur la fenêtre : l’icône d’application, la couleur d’arrière-plan de la fenêtre, le nom à afficher dans la barre de titre, entre autres choses. Plus important encore, il contient un pointeur de fonction vers votre procédure de fenêtre. L’exemple suivant montre une structure `WNDCLASSEX` type.

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

   Pour plus d’informations sur les champs de la structure ci-dessus, consultez [WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw).

1. Enregistrez le `WNDCLASSEX` avec Windows pour qu’il sache votre fenêtre et comment lui envoyer des messages. Utilisez la fonction [RegisterClassEx](/windows/win32/api/winuser/nf-winuser-registerclassexw) et passez la structure de classe de fenêtre comme argument. La macro `_T` est utilisée parce que nous utilisons le type de `TCHAR`.

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

   Cette fonction retourne un `HWND`, qui est un handle vers une fenêtre. Un descripteur est un peu comme un pointeur que Windows utilise pour effectuer le suivi des fenêtres ouvertes. Pour plus d'informations, consultez [Types de données Windows](/windows/win32/WinProg/windows-data-types).

1. À ce stade, la fenêtre a été créée, mais nous devons toujours indiquer à Windows de le rendre visible. C’est ce que fait ce code :

   ```cpp
   // The parameters to ShowWindow explained:
   // hWnd: the value returned from CreateWindow
   // nCmdShow: the fourth parameter from WinMain
   ShowWindow(hWnd,
      nCmdShow);
   UpdateWindow(hWnd);
   ```

   La fenêtre affichée n’a pas vraiment de contenu, car vous n’avez pas encore implémenté la fonction `WndProc`. En d’autres termes, l’application ne gère pas encore les messages que Windows envoie à présent à celle-ci.

1. Pour gérer les messages, nous commençons par ajouter une boucle de messages pour écouter les messages envoyés par Windows. Lorsque l’application reçoit un message, cette boucle la distribue à votre fonction `WndProc` pour être gérée. La boucle de message ressemble au code suivant.

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

   Un message important à gérer est le message [WM_PAINT](/windows/win32/gdi/wm-paint) . L’application reçoit le message `WM_PAINT` lorsqu’une partie de sa fenêtre affichée doit être mise à jour. L’événement peut se produire lorsqu’un utilisateur déplace une fenêtre devant votre fenêtre, puis la replace. Votre application ne sait pas quand ces événements se produisent. Seul Windows sait qu’il informe votre application d’un message de `WM_PAINT`. Quand la fenêtre est affichée pour la première fois, elle doit être mise à jour.

   Pour traiter un message `WM_PAINT` , appelez d’abord [BeginPaint](/windows/win32/api/winuser/nf-winuser-beginpaint), puis traitez toute la logique pour disposer le texte, les boutons et autres contrôles dans la fenêtre, puis appelez [EndPaint](/windows/win32/api/winuser/nf-winuser-endpaint). Pour l’application, la logique entre l’appel de début et l’appel de fin consiste à afficher la chaîne « Hello, Windows Desktop ! » dans la fenêtre. Dans le code suivant, notez que la fonction [TextOut](/windows/win32/api/wingdi/nf-wingdi-textoutw) est utilisée pour afficher la chaîne.

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

   `HDC` dans le code est un handle vers un contexte de périphérique (Device Context), qui est une structure de données utilisée par Windows pour permettre à votre application de communiquer avec le sous-système graphique. Les fonctions `BeginPaint` et `EndPaint` font que votre application se comporte comme un bon citoyen et n’utilise pas le contexte de périphérique plus longtemps que nécessaire. Les fonctions permettent de rendre le sous-système graphique disponible pour une utilisation par d’autres applications.

1. Une application gère généralement de nombreux autres messages. Par exemple, [WM_CREATE](/windows/win32/winmsg/wm-create) quand une fenêtre est créée pour la première fois et [WM_DESTROY](/windows/win32/winmsg/wm-destroy) quand la fenêtre est fermée. Le code suivant illustre une fonction `WndProc` basique mais complète.

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

Comme promis, voici le code complet de l’application opérationnelle.

### <a name="to-build-this-example"></a>Pour générer cet exemple

1. Supprimez le code que vous avez entré dans *HelloWindowsDesktop. cpp* dans l’éditeur. Copiez cet exemple de code, puis collez-le dans *HelloWindowsDesktop. cpp*:

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

1. Dans le menu **Générer** , choisissez **Générer la solution**. Les résultats de la compilation doivent apparaître dans la fenêtre **sortie** de Visual Studio.

   ![Générer le projet DesktopApp](../build/media/desktop-app-project-build-150.gif "Générer le projet DesktopApp")

1. Pour exécuter l’application, appuyez sur **F5**. Une fenêtre qui contient le texte « Hello, Windows Desktop ! » doit apparaître dans le coin supérieur gauche de l’affichage.

   ![Exécuter le projet DesktopApp](../build/media/desktop-app-project-run-157.PNG "Exécuter le projet DesktopApp")

Félicitations ! Vous avez terminé cette procédure pas à pas et créé une application de bureau Windows traditionnelle.

## <a name="see-also"></a>Voir aussi

[Applications de bureau Windows](../windows/windows-desktop-applications-cpp.md)
