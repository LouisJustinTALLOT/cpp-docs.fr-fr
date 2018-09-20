---
title: 'TN001 : Inscription de classe | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.registration
dev_langs:
- C++
helpviewer_keywords:
- TN001
- WNDCLASS [MFC]
- AfxRegisterClass function
ms.assetid: 1abf678e-f220-4606-85e0-03df32f64c54
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a6818cb66f7ae9498ca13ac895a84e3b22c0c482
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426092"
---
# <a name="tn001-window-class-registration"></a>TN001 : inscription de classe Windows

Cette note décrit les routines MFC qui s’inscrivent spéciale [WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576)es requis par Microsoft Windows. Spécifique `WNDCLASS` attributs utilisés par MFC et Windows sont décrits.

## <a name="the-problem"></a>Le problème

Les attributs d’un [CWnd](../mfc/reference/cwnd-class.md) de l’objet, comme un `HWND` gérer dans Windows, sont stockés dans deux emplacements : l’objet de fenêtre et la `WNDCLASS`. Le nom de la `WNDCLASS` est passé aux fonctions de création de fenêtres générales telles que [CWnd::Create](../mfc/reference/cwnd-class.md#create) et [CFrameWnd::Create](../mfc/reference/cframewnd-class.md#create) dans le *lpszClassName* paramètre.

Cela `WNDCLASS` doivent être inscrits via un des quatre moyens :

- Implicitement à l’aide d’une MFC fournie `WNDCLASS`.

- Implicitement par sous-classement d’un contrôle Windows (ou un autre contrôle).

- Explicitement en appelant la bibliothèque MFC [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass) ou [AfxRegisterClass](../mfc/reference/application-information-and-management.md#afxregisterclass).

- Explicitement en appelant la routine Windows [RegisterClass](https://msdn.microsoft.com/library/windows/desktop/ms633586).

## <a name="wndclass-fields"></a>Champs WNDCLASS

Le `WNDCLASS` structure se compose des différents champs qui décrivent une classe de fenêtre. Le tableau suivant affiche les champs et spécifie comment elles sont utilisées dans une application MFC :

|Champ|Description|
|-----------|-----------------|
|*lpfnWndProc*|procédure de fenêtre doit être un `AfxWndProc`|
|*membres cbClsExtra*|ne pas utilisé (doit être le zéro)|
|*cbWndExtra*|ne pas utilisé (doit être le zéro)|
|*hInstance*|automatiquement renseignée avec [AfxGetInstanceHandle](../mfc/reference/application-information-and-management.md#afxgetinstancehandle)|
|*hIcon*|icône de fenêtres frame, voir ci-dessous|
|*hCursor*|curseur lorsque la souris est sur la fenêtre, voir ci-dessous|
|*hbrBackground*|couleur d’arrière-plan, voir ci-dessous|
|*lpszMenuName*|ne pas utilisé (doit être le NULL)|
|*lpszClassName*|nom de classe, voir ci-dessous|

## <a name="provided-wndclasses"></a>Fourni WNDCLASSes

Versions antérieures de MFC (avant MFC 4.0), fournies plusieurs classes de fenêtre prédéfinies. Ces classes de fenêtre ne sont plus fournis par défaut. Les applications doivent utiliser `AfxRegisterWndClass` avec les paramètres appropriés.

Si l’application fournit une ressource avec l’ID de ressource spécifié (par exemple, AFX_IDI_STD_FRAME), MFC utilise cette ressource. Dans le cas contraire, il utilisera la ressource par défaut. Pour l’icône, l’icône d’application standard est utilisé, et pour le curseur, le curseur en flèche standard est utilisé.

Deux icônes prennent en charge les applications MDI avec des types de document unique : une icône pour l’application principale, l’autre icône de document/MDIChild sous forme d’icône windows. Pour plusieurs types de documents avec des icônes différentes, vous devez inscrire d’autres `WNDCLASS`es ou utilisez le [CFrameWnd::LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) (fonction).

`CFrameWnd::LoadFrame` enregistre un `WNDCLASS` à l’aide de l’ID d’icône que vous spécifiez en tant que premier paramètre et les attributs standards suivants :

- style de classe : CS_DBLCLKS &#124; CS_HREDRAW &#124; CS_VREDRAW ;

- icône AFX_IDI_STD_FRAME

- curseur en flèche

- Couleur d’arrière-plan COLOR_WINDOW

Les valeurs de couleur d’arrière-plan et de curseur pour le [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) ne sont pas utilisés depuis la zone cliente de la `CMDIFrameWnd` est complètement couvert par le **MDICLIENT** fenêtre. Microsoft ne conseille pas sous-classement le **MDICLIENT** fenêtre utilisez les couleurs standard et les types de curseurs lorsque cela est possible.

## <a name="subclassing-and-superclassing-controls"></a>Sous-classement et contrôles de surclassement

Si vous créez une sous-classe ou superclasse un Windows de contrôle (par exemple, [CButton](../mfc/reference/cbutton-class.md)) ensuite, votre classe obtient automatiquement le `WNDCLASS` attributs fournis dans l’implémentation Windows de ce contrôle.

## <a name="the-afxregisterwndclass-function"></a>La fonction AfxRegisterWndClass

MFC fournit une fonction d’assistance pour l’inscription d’une classe de fenêtre. Étant donné un ensemble d’attributs (style de classe de fenêtre, curseur, pinceau d’arrière-plan et icône), un nom synthétique est généré, et la classe de fenêtre qui en résulte est inscrit. Par exemple :

```
const char* AfxRegisterWndClass(UINT nClassStyle,
    HCURSOR hCursor,
    HBRUSH hbrBackground,
    HICON hIcon);
```

Cette fonction retourne une chaîne temporaire du nom de classe de fenêtres inscrites généré. Pour plus d’informations sur cette fonction, consultez [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass).

La chaîne retournée est un pointeur temporaire vers une mémoire tampon de chaîne statique. Il est valide jusqu’au prochain appel à `AfxRegisterWndClass`. Si vous souhaitez conserver cette chaîne autour, stockez-le dans un [CString](../atl-mfc-shared/using-cstring.md) variable, comme dans cet exemple :

```
CString strWndClass = AfxRegisterWndClass(CS_DBLCLK, ...);

...
CWnd* pWnd = new CWnd;
pWnd->Create(strWndClass, ...);

...
```

`AfxRegisterWndClass` lève une [CResourceException](../mfc/reference/cresourceexception-class.md) si la classe de fenêtre Échec d’inscription (en raison d’un paramètre incorrect, ou en dehors de la mémoire de Windows).

## <a name="the-registerclass-and-afxregisterclass-functions"></a>Les RegisterClass et les fonctions de AfxRegisterClass

Si vous voulez faire quoi que ce soit plus sophistiquées que celles qui `AfxRegisterWndClass` fournit, vous pouvez appeler l’API Windows `RegisterClass` ou la fonction MFC `AfxRegisterClass`. Le `CWnd`, [CFrameWnd](../mfc/reference/cframewnd-class.md) et [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) `Create` fonctions acceptent une *lpszClassName* nom de chaîne pour la classe de fenêtre comme premier paramètre. Vous pouvez utiliser tout nom de classe de fenêtres inscrites, quelle que soit la méthode que vous avez utilisé pour l’inscrire.

Il est important d’utiliser `AfxRegisterClass` (ou `AfxRegisterWndClass`) dans une DLL sur Win32. Win32 n’automatiquement annuler l’inscription de classes enregistrés par une DLL, vous devez le désinscrire explicitement classes lorsque la DLL est terminée. À l’aide de `AfxRegisterClass` au lieu de `RegisterClass` Ceci est géré automatiquement pour vous. `AfxRegisterClass` gère une liste de classes uniques inscrits par votre DLL et sera automatiquement annule leur enregistrement lors de la DLL se termine. Lorsque vous utilisez `RegisterClass` dans une DLL, vous devez vous assurer que toutes les classes sont annulées lorsque la DLL est terminée (dans votre [DllMain](/windows/desktop/Dlls/dllmain) fonction). Cela peut provoquer des `RegisterClass` Échec inattendu quand une autre application cliente tente d’utiliser votre DLL.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

