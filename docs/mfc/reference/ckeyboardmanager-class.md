---
title: Classe CKeyboardManager
ms.date: 11/04/2016
f1_keywords:
- CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CleanUp
- AFXKEYBOARDMANAGER/CKeyboardManager::FindDefaultAccelerator
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyHandled
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyPrintable
- AFXKEYBOARDMANAGER/CKeyboardManager::IsShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::LoadState
- AFXKEYBOARDMANAGER/CKeyboardManager::ResetAll
- AFXKEYBOARDMANAGER/CKeyboardManager::SaveState
- AFXKEYBOARDMANAGER/CKeyboardManager::ShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::TranslateCharToUpper
- AFXKEYBOARDMANAGER/CKeyboardManager::UpdateAccelTable
helpviewer_keywords:
- CKeyboardManager [MFC], CKeyboardManager
- CKeyboardManager [MFC], CleanUp
- CKeyboardManager [MFC], FindDefaultAccelerator
- CKeyboardManager [MFC], IsKeyHandled
- CKeyboardManager [MFC], IsKeyPrintable
- CKeyboardManager [MFC], IsShowAllAccelerators
- CKeyboardManager [MFC], LoadState
- CKeyboardManager [MFC], ResetAll
- CKeyboardManager [MFC], SaveState
- CKeyboardManager [MFC], ShowAllAccelerators
- CKeyboardManager [MFC], TranslateCharToUpper
- CKeyboardManager [MFC], UpdateAccelTable
ms.assetid: 4809ece6-89df-4479-8b53-9bf476ee107b
ms.openlocfilehash: 5d0f544943cc8584960bb2668ee7ce326547e2fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372317"
---
# <a name="ckeyboardmanager-class"></a>Classe CKeyboardManager

Gère les tables de touches de raccourci pour la fenêtre frame principale et les fenêtres frames enfants.

## <a name="syntax"></a>Syntaxe

```
class CKeyboardManager : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|||
|-|-|
|Nom|Description|
|[CKeyboardManager::CKeyboardManager](#ckeyboardmanager)|Construit un objet `CKeyboardManager`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|||
|-|-|
|Nom|Description|
|[CKeyboardManager::CleanUp](#cleanup)|Efface les tables clés de raccourci.|
|[CKeyboardManager::FindDefaultAccelerator](#finddefaultaccelerator)|Récupère la clé de raccourci par défaut pour la commande et la fenêtre spécifiées.|
|[CKeyboardManager::IsKeyHandled](#iskeyhandled)|Détermine si une clé est manipulée par la table d’accélérateur.|
|[CKeyboardManager::IsKeyPrintable](#iskeyprintable)|Indique si un personnage est imprimable.|
|[CKeyboardManager::IsShowAllCelerators](#isshowallaccelerators)|Indique si les menus affichent toutes les touches de raccourci pour une commande ou seulement la clé de raccourci par défaut.|
|[CKeyboardManager::LoadState](#loadstate)|Charge les tableaux clés raccourcis du registre Windows.|
|[CKeyboardManager::ResetAll](#resetall)|Recharge les tableaux clés raccourcis de la ressource d’application.|
|[CKeyboardManager::SaveState](#savestate)|Enregistre les tableaux clés de raccourci au registre Windows.|
|[CKeyboardManager::ShowAllAccelerators](#showallaccelerators)|Précise si le cadre affiche toutes les touches de raccourci pour toutes les commandes, ou une seule clé de raccourci pour chaque commande. Cette méthode n’affecte pas les commandes qui n’ont qu’une seule clé de raccourci associée.|
|[CKeyboardManager::TranslateCharToUpper](#translatechartoupper)|Convertit un personnage à son registre supérieur.|
|[CKeyboardManager::UpdateAccelTable](#updateacceltable)|Mise à jour d’un tableau de clés raccourci avec un nouveau tableau de clés raccourci.|

## <a name="remarks"></a>Notes

Les membres de cette classe vous permettent d’enregistrer et de charger des tables clés raccourcies au registre Windows, d’utiliser un modèle pour mettre à jour les tables clés raccourcies et de trouver la clé de raccourci par défaut pour une commande dans une fenêtre de cadre. En outre, `CKeyboardManager` l’objet vous permet de contrôler la façon dont les touches de raccourci sont affichées à l’utilisateur.

Vous ne devez `CKeyboardManager` pas créer un objet manuellement. Il sera créé automatiquement par le cadre de votre application. Toutefois, vous devez appeler [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager) pendant le processus d’initialisation de votre demande. Pour obtenir un pointeur au gestionnaire du clavier pour votre application, appelez [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager).

## <a name="example"></a>Exemple

L’exemple suivant montre comment récupérer `CKeyboardManager` un pointeur à un objet d’une `CWinAppEx` classe, et comment afficher toutes les touches de raccourci associées aux commandes de menu. Cet extrait de code fait partie de [l’échantillon de pages personnalisées](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxkeyboardmanager.h

## <a name="ckeyboardmanagerckeyboardmanager"></a><a name="ckeyboardmanager"></a>CKeyboardManager::CKeyboardManager

Construit un objet `CKeyboardManager`.

```
CKeyboardManager();
```

### <a name="remarks"></a>Notes

Dans la plupart des cas, `CKeyboardManager` vous n’avez pas à créer un directement. Par défaut, le cadre en crée un pour vous. Pour obtenir un `CKeyboardManager`pointeur à la , appelez [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager). Si vous créez un manuellement, vous devez l’initialiser avec la méthode [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager).

## <a name="ckeyboardmanagercleanup"></a><a name="cleanup"></a>CKeyboardManager::CleanUp

Libère les `CKeyboardManager` ressources et efface toutes les cartes clés de raccourci.

```
static void CleanUp();
```

### <a name="remarks"></a>Notes

Pour plus d’informations sur les touches de raccourci, voir [Keyboard et Mouse Customization](../../mfc/keyboard-and-mouse-customization.md).

Vous n’avez pas à appeler cette fonction lorsque votre application sort parce que le cadre l’appelle automatiquement lors de la sortie de l’application.

## <a name="ckeyboardmanagerfinddefaultaccelerator"></a><a name="finddefaultaccelerator"></a>CKeyboardManager::FindDefaultAccelerator

Récupère la clé de raccourci par défaut pour la commande et la fenêtre spécifiées.

```
static BOOL FindDefaultAccelerator(
    UINT uiCmd,
    CString& str,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>Paramètres

*uiCmd uiCmd*<br/>
[dans] L’id de commande.

*Str*<br/>
[out] Une référence `CString` à un objet.

*pWndFrame (en)*<br/>
[dans] Un pointeur à une fenêtre de cadre.

*bIsDefaultFrame*<br/>
[dans] Précise si la fenêtre de cadre est la fenêtre de cadre par défaut.

### <a name="return-value"></a>Valeur de retour

Nonzero si le raccourci est trouvé; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode recherche la commande spécifiée par *uiCmd* et récupère la clé de raccourci par défaut. Ensuite, la méthode prend la chaîne associée à cette clé de raccourci et écrit la valeur au paramètre *str.*

## <a name="ckeyboardmanageriskeyhandled"></a><a name="iskeyhandled"></a>CKeyboardManager::IsKeyHandled

Détermine si la clé spécifiée est gérée par la [classe CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md).

```
static BOOL __stdcall IsKeyHandled(
    WORD nKey,
    BYTE fVirt,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*nKey (en)*|[dans] La clé à vérifier.|
|*fVirt*|[dans] Spécifie le comportement de la clé de raccourci. Pour une liste de valeurs possibles, voir [ACCEL Structure](/windows/win32/api/winuser/ns-winuser-accel).|
|*pWndFrame (en)*|[dans] Une fenêtre de cadre. Cette méthode détermine si une clé de raccourci est manipulée dans ce cadre.|
|*bIsDefaultFrame*|[dans] Un paramètre Boolean qui indique si *pWndFrame* est la fenêtre de cadre par défaut.|

### <a name="return-value"></a>Valeur de retour

VRAI si la clé de raccourci est manipulée. FALSE si la clé n’est pas manipulée ou si *pWndFrame* est NULL.

### <a name="remarks"></a>Notes

Les paramètres d’entrée doivent correspondre à l’entrée dans le tableau d’accélérateur à la fois pour *nKey* et *fVirt* pour déterminer si une clé de raccourci est manipulée dans *pWndFrame*.

## <a name="ckeyboardmanageriskeyprintable"></a><a name="iskeyprintable"></a>CKeyboardManager::IsKeyPrintable

Indique si un personnage est imprimable.

```
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*Nchar*|[dans] Le caractère que cette méthode vérifie.|

### <a name="return-value"></a>Valeur de retour

Nonzero si le personnage est imprimable, zéro si ce n’est pas le cas.

### <a name="remarks"></a>Notes

Cette méthode échoue si un appel à [GetKeyboardState](/windows/win32/api/winuser/nf-winuser-getkeyboardstate) échoue.

## <a name="ckeyboardmanagerisshowallaccelerators"></a><a name="isshowallaccelerators"></a>CKeyboardManager::IsShowAllCelerators

Indique si les menus affichent toutes les touches de raccourci associées aux commandes de menu ou seulement les clés de raccourci par défaut.

```
static BOOL IsShowAllAccelerators();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’application répertorie toutes les clés de raccourci pour les commandes de menu; 0 si l’application affiche uniquement les clés de raccourci par défaut.

### <a name="remarks"></a>Notes

L’application répertorie les clés de raccourci pour les commandes de menu dans la barre de menu. Utilisez la fonction [CKeyboardManager::ShowAllAccelerators](#showallaccelerators) pour contrôler si l’application répertorie toutes les clés de raccourci ou tout simplement les clés de raccourci par défaut.

## <a name="ckeyboardmanagerloadstate"></a><a name="loadstate"></a>CKeyboardManager::LoadState

Charge les tableaux clés raccourcis du registre Windows.

```
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
[dans] Le chemin `CKeyboardManager` du registre où les données sont enregistrées.

*pDefaultFrame*<br/>
[dans] Un pointeur à une fenêtre de cadre à utiliser comme fenêtre par défaut.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’état a été chargé avec succès ou 0 autrement.

### <a name="remarks"></a>Notes

Si le paramètre *lpszProfileName* est NULL, cette `CKeyboardManager` méthode vérifie l’emplacement du registre par défaut pour les données. L’emplacement du registre par défaut est spécifié par la [classe CWinAppEx](../../mfc/reference/cwinappex-class.md). Les données doivent être précédemment écrites avec la méthode [CKeyboardManager::SaveState](#savestate).

Si vous ne spécifiez pas une fenêtre par défaut, la fenêtre principale de votre application sera utilisée.

## <a name="ckeyboardmanagerresetall"></a><a name="resetall"></a>CKeyboardManager::ResetAll

Recharge les tableaux clés raccourcis de la ressource d’application.

```
void ResetAll();
```

### <a name="remarks"></a>Notes

Cette fonction efface les raccourcis `CKeyboardManager` stockés dans l’instance. Il rechargera ensuite l’état du gestionnaire du clavier à partir de la ressource d’application.

## <a name="ckeyboardmanagersavestate"></a><a name="savestate"></a>CKeyboardManager::SaveState

Enregistre les tableaux clés de raccourci au registre Windows.

```
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
[dans] La voie du `CKeyboardManager` registre pour sauver l’État.

*pDefaultFrame*<br/>
[dans] Un pointeur vers une fenêtre de cadre qui devient la fenêtre par défaut.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’état de gestionnaire de clavier a été sauvé avec succès, ou 0 autrement.

### <a name="remarks"></a>Notes

Si le paramètre *lpszProfileName* est NULL, cette méthode écrira l’état `CKeyboardManager` à l’emplacement par défaut spécifié par la classe [CWinAppEx](../../mfc/reference/cwinappex-class.md). Si vous spécifiez un emplacement, vous pouvez charger les données plus tard en utilisant la méthode [CKeyboardManager::LoadState](#loadstate).

Si vous ne spécifiez pas une fenêtre par défaut, la fenêtre principale sera utilisée comme fenêtre par défaut.

## <a name="ckeyboardmanagershowallaccelerators"></a><a name="showallaccelerators"></a>CKeyboardManager::ShowAllAccelerators

Affiche toutes les clés de raccourci associées aux commandes de menu.

```
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```

### <a name="parameters"></a>Paramètres

*bShowAll (en)*<br/>
[dans] Si TRUE, toutes les touches de raccourci seront affichées. Si FALSE, seule la première clé de raccourci sera affichée.

*lpszDelimiter*<br/>
[dans] Une ficelle à insérer entre les touches de raccourci. Ce délimitateur n’a aucun effet si une seule clé de raccourci est affichée.

### <a name="remarks"></a>Notes

Par défaut, si une commande a plus d’une clé de raccourci qui lui est associée, seule la première clé de raccourci sera affichée. Cette fonction vous permet d’énumérer toutes les clés de raccourci associées à toutes les commandes.

Les touches de raccourci seront répertoriées à côté de la commande dans la barre de menu. Si toutes les touches de raccourci sont affichées, la chaîne fournie par *lpszDelimiter* séparera les touches individuelles de raccourci.

## <a name="ckeyboardmanagertranslatechartoupper"></a><a name="translatechartoupper"></a>CKeyboardManager::TranslateCharToUpper

Convertit un personnage à son registre supérieur.

```
static UINT TranslateCharToUpper(const UINT nChar);
```

### <a name="parameters"></a>Paramètres

*Nchar*<br/>
[dans] Le personnage à convertir.

### <a name="return-value"></a>Valeur de retour

Le caractère qui est le registre supérieur du paramètre d’entrée.

## <a name="ckeyboardmanagerupdateacceltable"></a><a name="updateacceltable"></a>CKeyboardManager::UpdateAccelTable

Mise à jour d’un tableau de clés raccourci avec un nouveau tableau de clés raccourci.

```
BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,
    LPACCEL lpAccel,
    int nSize,
    CFrameWnd* pDefaultFrame = NULL);

BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,
    HACCEL hAccelNew,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Paramètres

*pTemplate (en)*<br/>
[dans] Un pointeur vers un modèle de document.

*lpAccel*<br/>
[dans] Un pointeur vers la nouvelle clé de raccourci.

*nSize (en)*<br/>
[dans] La taille de la nouvelle table de raccourci.

*pDefaultFrame*<br/>
[dans] Un pointeur à la fenêtre de cadre par défaut.

*hAccelNew*<br/>
[dans] Une poignée à la nouvelle table de raccourci.

### <a name="return-value"></a>Valeur de retour

Nonzero si la méthode est réussie; sinon 0.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour remplacer la table de raccourci existante par de nouvelles touches de raccourci pour plusieurs objets de fenêtre de cadre. La fonction reçoit un modèle de document comme paramètre pour obtenir l’accès à tous les objets de fenêtre de cadre connectés au modèle de document donné.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx, classe](../../mfc/reference/cwinappex-class.md)<br/>
[CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)<br/>
[Personnalisation du clavier et de la souris](../../mfc/keyboard-and-mouse-customization.md)
