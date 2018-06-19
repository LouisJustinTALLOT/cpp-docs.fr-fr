---
title: 'TN001 : Inscription de classe | Documents Microsoft'
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
ms.openlocfilehash: 245ffcb66223813c7146c50c964cd97203ed8d53
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383852"
---
# <a name="tn001-window-class-registration"></a>TN001 : inscription de classe Windows
Cette note décrit les routines MFC qui inscrivent spéciale [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576)es requis par Microsoft Windows. Spécifique `WNDCLASS` attributs utilisés par MFC et Windows sont décrites.  
  
## <a name="the-problem"></a>Le problème  
 Les attributs d’un [CWnd](../mfc/reference/cwnd-class.md) de l’objet, comme un `HWND` gérer dans Windows, sont stockées dans deux emplacements : l’objet de fenêtre et la `WNDCLASS`. Le nom de la `WNDCLASS` est transmis aux fonctions de création de fenêtres générales telles que [CWnd::Create](../mfc/reference/cwnd-class.md#create) et [CFrameWnd::Create](../mfc/reference/cframewnd-class.md#create) dans le `lpszClassName` paramètre.  
  
 Cela `WNDCLASS` doivent être inscrits via une des quatre manières :  
  
-   Implicitement en utilisant un MFC fourni `WNDCLASS`.  
  
-   Implicitement par le sous-classement d’un contrôle Windows (ou autres contrôles).  
  
-   Explicitement en appelant la bibliothèque MFC [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass) ou [AfxRegisterClass](../mfc/reference/application-information-and-management.md#afxregisterclass).  
  
-   Explicitement en appelant la routine Windows [RegisterClass](http://msdn.microsoft.com/library/windows/desktop/ms633586).  
  
## <a name="wndclass-fields"></a>Champs WNDCLASS  
 Le `WNDCLASS` se compose de plusieurs champs qui décrivent une classe de fenêtre. Le tableau suivant affiche les champs et spécifie la façon dont ils sont utilisés dans une application MFC :  
  
|Champ|Description|  
|-----------|-----------------|  
|`lpfnWndProc`|procédure de fenêtre doit être un `AfxWndProc`|  
|`cbClsExtra`|non utilisé (doit être le zéro)|  
|`cbWndExtra`|non utilisé (doit être le zéro)|  
|`hInstance`|automatiquement renseigné avec [AfxGetInstanceHandle](../mfc/reference/application-information-and-management.md#afxgetinstancehandle)|  
|`hIcon`|icône de fenêtres frame, voir ci-dessous|  
|`hCursor`|curseur lorsque la souris est au-dessus de la fenêtre, consultez la section ci-dessous|  
|`hbrBackground`|couleur d’arrière-plan, voir ci-dessous|  
|`lpszMenuName`|non utilisé (doit être le NULL)|  
|`lpszClassName`|nom de classe, voir ci-dessous|  
  
## <a name="provided-wndclasses"></a>Fourni WNDCLASSes  
 Les versions antérieures de MFC (avant MFC 4.0), fourni plusieurs classes de fenêtre prédéfinis. Ces classes de fenêtre ne sont plus fournis par défaut. Les applications doivent utiliser `AfxRegisterWndClass` avec les paramètres appropriés.  
  
 Si l’application fournit une ressource avec l’ID de ressource spécifié (par exemple, AFX_IDI_STD_FRAME), MFC utilise cette ressource. Dans le cas contraire, il utilisera la ressource par défaut. Pour l’icône, l’icône d’application standard est utilisée, et pour le curseur, le curseur de flèche standard est utilisé.  
  
 Deux icônes prennent en charge les applications MDI avec des types de document unique : une icône de l’application principale, l’autre icône de document/MDIChild sous forme d’icône windows. Pour plusieurs types de document avec des icônes différentes, vous devez inscrire d’autres `WNDCLASS`es ou utilisez le [CFrameWnd::LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) (fonction).  
  
 `CFrameWnd::LoadFrame` enregistre un `WNDCLASS` à l’aide de l’ID d’icône que vous spécifiez en tant que premier paramètre et les attributs standards suivants :  
  
-   style de classe : CS_DBLCLKS &#124; CS_HREDRAW &#124; CS_VREDRAW ;  
  
-   icône AFX_IDI_STD_FRAME  
  
-   curseur de flèche  
  
-   Couleur d’arrière-plan COLOR_WINDOW  
  
 Les valeurs de couleur d’arrière-plan et de curseur pour la [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) ne sont pas utilisés depuis la zone cliente de la `CMDIFrameWnd` est complètement couvert par le **MDICLIENT** fenêtre. Microsoft déconseille sous-classement le **MDICLIENT** fenêtre donc utiliser que les couleurs standard et les types de curseur lorsque cela est possible.  
  
## <a name="subclassing-and-superclassing-controls"></a>Le sous-classement et contrôles de surclasser  
 Si vous créez une sous-classe ou superclasse Windows de contrôle (par exemple, [CButton](../mfc/reference/cbutton-class.md)) puis votre classe obtient automatiquement les `WNDCLASS` attributs fournis dans l’implémentation Windows de ce contrôle.  
  
## <a name="the-afxregisterwndclass-function"></a>La fonction AfxRegisterWndClass  
 MFC fournit une fonction d’assistance pour l’inscription d’une classe de fenêtre. Étant donné un ensemble d’attributs (style de classe de fenêtre, curseur, pinceau d’arrière-plan et icône), un nom synthétique est généré et la classe de fenêtre qui en résulte est enregistrée. Par exemple :  
  
```  
const char* AfxRegisterWndClass(UINT nClassStyle,
    HCURSOR hCursor,
    HBRUSH hbrBackground,
    HICON hIcon);
```  
  
 Cette fonction retourne une chaîne temporaire du nom de classe de fenêtre inscrits généré. Pour plus d’informations sur cette fonction, consultez [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass).  
  
 La chaîne retournée est un pointeur temporaire vers une mémoire tampon de chaîne statique. Il n’est valide jusqu’au prochain appel à `AfxRegisterWndClass`. Si vous souhaitez conserver cette chaîne autour, stockez-le dans un [CString](../atl-mfc-shared/using-cstring.md) variable, comme dans cet exemple :  
  
```  
CString strWndClass = AfxRegisterWndClass(CS_DBLCLK, ...);

...  
CWnd* pWnd = new CWnd;  
pWnd->Create(strWndClass, ...);

...  
```  
  
 `AfxRegisterWndClass` lève un [CResourceException](../mfc/reference/cresourceexception-class.md) si la classe de fenêtre Impossible d’enregistrer (en raison d’un paramètre incorrect, ou la mémoire de Windows).  
  
## <a name="the-registerclass-and-afxregisterclass-functions"></a>Les RegisterClass et les fonctions de AfxRegisterClass  
 Si vous voulez faire quoi que ce soit plus sophistiquée que ce que `AfxRegisterWndClass` fournit, vous pouvez appeler l’API Windows `RegisterClass` ou la fonction MFC `AfxRegisterClass`. Le `CWnd`, [CFrameWnd](../mfc/reference/cframewnd-class.md) et [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) `Create` fonctions acceptent un `lpszClassName` nom de chaîne pour la classe de fenêtre comme premier paramètre. Vous pouvez utiliser tout nom de classe de fenêtre inscrit, quelle que soit la méthode utilisée pour l’inscrire.  
  
 Il est important d’utiliser `AfxRegisterClass` (ou `AfxRegisterWndClass`) dans une DLL sur Win32. Win32 n’automatiquement annuler l’inscription de classes enregistrés par une DLL, vous devez le désinscrire explicitement classes lorsque la DLL est terminée. À l’aide de `AfxRegisterClass` au lieu de `RegisterClass` Ceci est géré automatiquement pour vous. `AfxRegisterClass` gère une liste de classes uniques enregistrés par votre DLL ainsi automatiquement annulera les lorsque la DLL se termine. Lorsque vous utilisez `RegisterClass` dans une DLL, vous devez vous assurer que toutes les classes sont annulées lorsque la DLL est arrêtée (dans votre [DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583) fonction). Cela peut provoquer des `RegisterClass` Échec inattendu lorsqu’une autre application cliente essaie d’utiliser votre DLL.  
  
## <a name="see-also"></a>Voir aussi  
 [Notes techniques par numéro](../mfc/technical-notes-by-number.md)   
 [Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

