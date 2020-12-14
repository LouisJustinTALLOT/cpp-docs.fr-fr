---
description: 'En savoir plus sur : TN001 : inscription des classes de fenêtre'
title: 'TN001 : inscription de classe Windows'
ms.date: 11/04/2016
f1_keywords:
- vc.registration
helpviewer_keywords:
- TN001
- WNDCLASS [MFC]
- AfxRegisterClass function
ms.assetid: 1abf678e-f220-4606-85e0-03df32f64c54
ms.openlocfilehash: fc54b6f783a50bb35f87f542772b9a1921f1f7b7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216104"
---
# <a name="tn001-window-class-registration"></a>TN001 : inscription de classe Windows

Cette note décrit les routines MFC qui inscrivent les [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw)s spéciaux nécessaires à Microsoft Windows. `WNDCLASS`Les attributs spécifiques utilisés par MFC et Windows sont décrits.

## <a name="the-problem"></a>Le problème

Les attributs d’un objet [CWnd](../mfc/reference/cwnd-class.md) , comme un `HWND` handle dans Windows, sont stockés à deux emplacements : l’objet Window et `WNDCLASS` . Le nom du `WNDCLASS` est passé aux fonctions de création de fenêtre générales telles que [CWnd :: Create](../mfc/reference/cwnd-class.md#create) et [CFrameWnd :: Create](../mfc/reference/cframewnd-class.md#create) dans le paramètre *lpszClassName* .

Celui-ci `WNDCLASS` doit être enregistré à l’aide de l’une des quatre méthodes suivantes :

- Implicitement à l’aide d’un MFC fourni `WNDCLASS` .

- Implicitement en sous-classant un contrôle Windows (ou un autre contrôle).

- Explicitement en appelant les MFC [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass) ou [AfxRegisterClass](../mfc/reference/application-information-and-management.md#afxregisterclass).

- Explicitement en appelant la routine Windows [registerClass](/windows/win32/api/winuser/nf-winuser-registerclassw).

## <a name="wndclass-fields"></a>Champs WNDCLASS

La `WNDCLASS` structure se compose de différents champs qui décrivent une classe de fenêtre. Le tableau suivant présente les champs et spécifie comment ils sont utilisés dans une application MFC :

|Champ|Description|
|-----------|-----------------|
|*lpfnWndProc*|la procédure de fenêtre doit être un `AfxWndProc`|
|*cbClsExtra*|non utilisé (doit être égal à zéro)|
|*cbWndExtra*|non utilisé (doit être égal à zéro)|
|*hInstance*|renseigné automatiquement avec [AfxGetInstanceHandle](../mfc/reference/application-information-and-management.md#afxgetinstancehandle)|
|*hIcon*|icône pour les fenêtres Frame, voir ci-dessous|
|*hCursor*|curseur pour lorsque la souris est sur la fenêtre, voir ci-dessous|
|*hbrBackground*|couleur d’arrière-plan, voir ci-dessous|
|*lpszMenuName*|non utilisé (doit avoir la valeur NULL)|
|*lpszClassName*|nom de la classe, voir ci-dessous|

## <a name="provided-wndclasses"></a>WNDCLASSes fourni

Les versions antérieures de MFC (avant MFC 4,0) fournissaient plusieurs classes de fenêtres prédéfinies. Ces classes de fenêtres ne sont plus fournies par défaut. Les applications doivent utiliser `AfxRegisterWndClass` avec les paramètres appropriés.

Si l’application fournit une ressource avec l’ID de ressource spécifié (par exemple, AFX_IDI_STD_FRAME), MFC utilise cette ressource. Dans le cas contraire, elle utilisera la ressource par défaut. Pour l’icône, l’icône d’application standard est utilisée, et pour le curseur, le curseur à flèche standard est utilisé.

Deux icônes prennent en charge les applications MDI avec des types de documents uniques : une icône pour l’application principale, l’autre icône pour sous forme document/MDIChild Windows. Pour plusieurs types de documents avec des icônes différentes, vous devez inscrire des `WNDCLASS` e/s supplémentaires ou utiliser la fonction [CFrameWnd :: LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) .

`CFrameWnd::LoadFrame` inscrit un `WNDCLASS` à l’aide de l’ID d’icône que vous spécifiez comme premier paramètre et des attributs standard suivants :

- style de classe : CS_DBLCLKS &#124; CS_HREDRAW &#124; CS_VREDRAW ;

- icône AFX_IDI_STD_FRAME

- Curseur en forme de flèche

- Couleur d’arrière-plan COLOR_WINDOW

Les valeurs de la couleur d’arrière-plan et du curseur du [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) ne sont pas utilisées, car la zone cliente du `CMDIFrameWnd` est entièrement couverte par la fenêtre **MdiClient** . Microsoft n’encourage pas les sous-classements de la fenêtre **MdiClient** . Utilisez donc les couleurs et les types de curseurs standard lorsque cela est possible.

## <a name="subclassing-and-superclassing-controls"></a>Contrôles de sous-classe et de superclassement

Si vous sous-classez ou superclassez un contrôle Windows (par exemple, [CButton](../mfc/reference/cbutton-class.md)), votre classe obtient automatiquement les `WNDCLASS` attributs fournis dans l’implémentation Windows de ce contrôle.

## <a name="the-afxregisterwndclass-function"></a>Fonction AfxRegisterWndClass

MFC fournit une fonction d’assistance pour l’inscription d’une classe de fenêtre. À partir d’un ensemble d’attributs (style de classe de fenêtre, curseur, pinceau d’arrière-plan et icône), un nom synthétique est généré et la classe de fenêtre obtenue est inscrite. Par exemple :

```
const char* AfxRegisterWndClass(UINT nClassStyle,
    HCURSOR hCursor,
    HBRUSH hbrBackground,
    HICON hIcon);
```

Cette fonction retourne une chaîne temporaire du nom de la classe de fenêtre inscrite générée. Pour plus d’informations sur cette fonction, consultez [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass).

La chaîne retournée est un pointeur temporaire vers une mémoire tampon de chaîne statique. Elle est valide jusqu’au prochain appel à `AfxRegisterWndClass` . Si vous souhaitez conserver cette chaîne, stockez-la dans une variable [CString](../atl-mfc-shared/using-cstring.md) , comme dans cet exemple :

```
CString strWndClass = AfxRegisterWndClass(CS_DBLCLK, ...);

...
CWnd* pWnd = new CWnd;
pWnd->Create(strWndClass, ...);

...
```

`AfxRegisterWndClass` lèvera un [CResourceException](../mfc/reference/cresourceexception-class.md) si la classe de fenêtre n’a pas pu être inscrite (en raison de paramètres incorrects ou de la mémoire insuffisante de Windows).

## <a name="the-registerclass-and-afxregisterclass-functions"></a>Fonctions RegisterClass et AfxRegisterClass

Si vous souhaitez faire quelque chose de plus sophistiqué que ce que `AfxRegisterWndClass` fournit, vous pouvez appeler l’API Windows `RegisterClass` ou la fonction MFC `AfxRegisterClass` . Les `CWnd` fonctions, [CFrameWnd](../mfc/reference/cframewnd-class.md) et [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) `Create` prennent un nom de chaîne *lpszClassName* pour la classe de fenêtre comme premier paramètre. Vous pouvez utiliser n’importe quel nom de classe de fenêtre inscrite, quelle que soit la méthode utilisée pour l’inscrire.

Il est important d’utiliser `AfxRegisterClass` (ou `AfxRegisterWndClass` ) dans une dll sur Win32. Win32 n’annule pas automatiquement l’inscription des classes inscrites par une DLL. vous devez donc annuler explicitement l’inscription des classes lorsque la DLL est terminée. À l’aide `AfxRegisterClass` de, au lieu de `RegisterClass` cela, est géré automatiquement pour vous. `AfxRegisterClass` gère une liste de classes uniques inscrites par votre DLL et les annule automatiquement à l’arrêt de la DLL. Lorsque vous utilisez `RegisterClass` dans une dll, vous devez vous assurer que toutes les classes sont désinscrites lorsque la dll est terminée (dans votre fonction [DllMain](/windows/win32/Dlls/dllmain) ). Si vous ne le faites pas, vous risquez `RegisterClass` d’échouer de manière inattendue lorsqu’une autre application cliente tente d’utiliser votre dll.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
