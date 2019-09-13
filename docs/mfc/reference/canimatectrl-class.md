---
title: CAnimateCtrl, classe
ms.date: 11/04/2016
f1_keywords:
- CAnimateCtrl
- AFXCMN/CAnimateCtrl
- AFXCMN/CAnimateCtrl::CAnimateCtrl
- AFXCMN/CAnimateCtrl::Close
- AFXCMN/CAnimateCtrl::Create
- AFXCMN/CAnimateCtrl::CreateEx
- AFXCMN/CAnimateCtrl::IsPlaying
- AFXCMN/CAnimateCtrl::Open
- AFXCMN/CAnimateCtrl::Play
- AFXCMN/CAnimateCtrl::Seek
- AFXCMN/CAnimateCtrl::Stop
helpviewer_keywords:
- CAnimateCtrl [MFC], CAnimateCtrl
- CAnimateCtrl [MFC], Close
- CAnimateCtrl [MFC], Create
- CAnimateCtrl [MFC], CreateEx
- CAnimateCtrl [MFC], IsPlaying
- CAnimateCtrl [MFC], Open
- CAnimateCtrl [MFC], Play
- CAnimateCtrl [MFC], Seek
- CAnimateCtrl [MFC], Stop
ms.assetid: 5e8eb1bd-96b7-47b8-8de2-6bcbb3cc299b
ms.openlocfilehash: 18adead999f26768ae669d3a829b557bf9632a29
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177445"
---
# <a name="canimatectrl-class"></a>CAnimateCtrl, classe

Fournit les fonctionnalités du contrôle commun d'animation Windows.

## <a name="syntax"></a>Syntaxe

```
class CAnimateCtrl : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAnimateCtrl::CAnimateCtrl](#canimatectrl)|Construit un objet `CAnimateCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimateCtrl::Close](#close)|Ferme le clip AVI.|
|[CAnimateCtrl::Create](#create)|Crée un contrôle d’animation et l’attache à un `CAnimateCtrl` objet.|
|[CAnimateCtrl::CreateEx](#createex)|Crée un contrôle d’animation avec les styles étendus Windows spécifiés et l’attache `CAnimateCtrl` à un objet.|
|[CAnimateCtrl::IsPlaying](#isplaying)|Indique si un clip AVI (Audio-Video entrelacé) est en lecture.|
|[CAnimateCtrl::Open](#open)|Ouvre un clip AVI à partir d’un fichier ou d’une ressource et affiche la première image.|
|[CAnimateCtrl::Play](#play)|Lit le clip AVI sans son.|
|[CAnimateCtrl::Seek](#seek)|Affiche une image unique sélectionnée du clip AVI.|
|[CAnimateCtrl::Stop](#stop)|Arrête la diffusion du clip AVI.|

## <a name="remarks"></a>Notes

Ce contrôle (et par conséquent `CAnimateCtrl` la classe) est uniquement disponible pour les programmes qui s’exécutent sous Windows 95, Windows 98 et Windows NT version 3,51 et ultérieure.

Un contrôle d’animation est une fenêtre rectangulaire qui affiche un clip au format AVI (Audio Video entrelacé), le format vidéo/audio Windows standard. Un clip AVI est une série de frames bitmap, comme un film.

Les contrôles d’animation ne peuvent lire que des clips AVI simples. Plus précisément, les clips à lire par un contrôle d’animation doivent remplir les conditions suivantes :

- Il doit y avoir exactement un flux vidéo et il doit comporter au moins un frame.

- Le fichier peut contenir au plus deux flux (en général, l’autre flux, le cas échéant, est un flux audio, bien que le contrôle d’animation ignore les informations audio).

- Le clip doit être décompressé ou compressé avec la compression RLE8.

- Aucune modification de palette n’est autorisée dans le flux vidéo.

Vous pouvez ajouter le clip AVI à votre application en tant que ressource AVI, ou il peut accompagner votre application sous la forme d’un fichier AVI distinct.

Étant donné que votre thread continue de s’exécuter pendant l’affichage du clip AVI, une utilisation courante pour un contrôle d’animation consiste à indiquer l’activité système pendant une opération de longue durée. Par exemple, la boîte de dialogue Rechercher de l’Explorateur de fichiers affiche une loupe mobile lorsque le système recherche un fichier.

Si vous créez un `CAnimateCtrl` objet dans une boîte de dialogue ou à partir d’une ressource de boîte de dialogue à l’aide de l’éditeur de boîtes de dialogue, il est automatiquement détruit lorsque l’utilisateur ferme la boîte de dialogue.

Si vous créez un `CAnimateCtrl` objet dans une fenêtre, vous devrez peut-être le détruire. Si vous créez l' `CAnimateCtrl` objet sur la pile, il est détruit automatiquement. Si vous créez l' `CAnimateCtrl` objet sur le tas à l’aide de la fonction **New** , vous devez appeler **Delete** sur l’objet pour le détruire. Si vous dérivez une nouvelle `CAnimateCtrl` classe de et que vous allouez de la mémoire dans `CAnimateCtrl` cette classe, substituez le destructeur pour supprimer les allocations.

Pour plus d’informations sur `CAnimateCtrl`l’utilisation de, consultez [contrôles](../../mfc/controls-mfc.md) et [utilisation de CAnimateCtrl](../../mfc/using-canimatectrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CAnimateCtrl`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxcmn.h

##  <a name="canimatectrl"></a>  CAnimateCtrl::CAnimateCtrl

Construit un objet `CAnimateCtrl`.

```
CAnimateCtrl();
```

### <a name="remarks"></a>Notes

Vous devez appeler la fonction membre [Create](#create) avant de pouvoir effectuer d’autres opérations sur l’objet que vous créez.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]

##  <a name="close"></a>  CAnimateCtrl::Close

Ferme le clip AVI précédemment ouvert dans le contrôle d’animation (le cas échéant) et le supprime de la mémoire.

```
BOOL Close();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CAnimateCtrl :: CAnimateCtrl](#canimatectrl).

##  <a name="create"></a>  CAnimateCtrl::Create

Crée un contrôle d’animation et l’attache à un `CAnimateCtrl` objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Spécifie le style du contrôle d’animation. Appliquez n’importe quelle combinaison des styles Windows décrits dans la section Notes ci-dessous et les styles de contrôle d’animation décrits dans [styles de contrôle d’animation](/windows/win32/Controls/animation-control-styles) dans le SDK Windows.

*rect*<br/>
Spécifie la position et la taille du contrôle d’animation. Il peut s’agir d’un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) ou d’une structure [Rect](/windows/win32/api/windef/ns-windef-rect) .

*pParentWnd*<br/>
Spécifie la fenêtre parente du contrôle d’animation `CDialog`, généralement. Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle d’animation.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Vous construisez `CAnimateCtrl` un en deux étapes. Tout d’abord, appelez le constructeur, puis `Create`appelez, qui crée le contrôle d’animation et l’attache à `CAnimateCtrl` l’objet.

Appliquez les [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) suivants à un contrôle d’animation.

- WS_CHILD toujours

- WS_VISIBLE généralement

- WS_DISABLED rarement

Si vous souhaitez utiliser des styles Windows étendus avec votre contrôle d’animation, appelez [CreateEx](#createex) au lieu de `Create`.

Outre les styles de fenêtre listés ci-dessus, vous pouvez appliquer un ou plusieurs styles de contrôle d’animation à un contrôle d’animation. Pour plus d’informations sur les [styles de contrôle d’animation](/windows/win32/Controls/animation-control-styles), consultez la SDK Windows.

### <a name="example"></a>Exemples

  Consultez l’exemple de [CAnimateCtrl :: CAnimateCtrl](#canimatectrl).

##  <a name="createex"></a>  CAnimateCtrl::CreateEx

Crée un contrôle (une fenêtre enfant) et l’associe à `CAnimateCtrl` l’objet.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwExStyle*<br/>
Spécifie le style étendu du contrôle en cours de création. Pour obtenir la liste des styles Windows étendus, consultez le paramètre *dwExStyle* pour [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) dans le SDK Windows.

*dwStyle*<br/>
Spécifie le style du contrôle d’animation. Appliquez toute combinaison de styles de contrôle de fenêtre et d’animation décrite dans [styles de contrôle d’animation](/windows/win32/Controls/animation-control-styles) dans le SDK Windows.

*rect*<br/>
Référence à une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) décrivant la taille et la position de la fenêtre à créer, en coordonnées clientes de *pParentWnd*.

*pParentWnd*<br/>
Pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
ID de la fenêtre enfant du contrôle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de [Create](#create) pour appliquer des styles Windows étendus, spécifiés par la préface de style étendu Windows **WS_EX_** .

##  <a name="isplaying"></a>  CAnimateCtrl::IsPlaying

Indique si un clip AVI (Audio-Video entrelacé) est en lecture.

```
BOOL IsPlaying() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si un clip AVI est lu ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [ACM_ISPLAYING](/windows/win32/Controls/acm-isplaying) , qui est décrit dans le SDK Windows.

##  <a name="open"></a>  CAnimateCtrl::Open

Appelez cette fonction pour ouvrir un clip AVI et afficher son premier frame.

```
BOOL Open(LPCTSTR lpszFileName);
BOOL Open(UINT nID);
```

### <a name="parameters"></a>Paramètres

*lpszFileName*<br/>
`CString` Objet ou pointeur vers une chaîne se terminant par un caractère null qui contient le nom du fichier AVI ou le nom d’une ressource avi. Si ce paramètre a la valeur NULL, le système ferme le clip AVI précédemment ouvert pour le contrôle d’animation, le cas échéant.

*nID*<br/>
Identificateur de ressource AVI. Si ce paramètre a la valeur NULL, le système ferme le clip AVI précédemment ouvert pour le contrôle d’animation, le cas échéant.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

La ressource AVI est chargée à partir du module qui a créé le contrôle d’animation.

`Open`ne prend pas en charge le son dans un clip AVI. vous ne pouvez ouvrir que des clips AVI en mode silencieux.

Si le contrôle d’animation a `ACS_AUTOPLAY` le style, le contrôle d’animation commence automatiquement la diffusion du clip immédiatement après son ouverture. Il continuera de lire le clip en arrière-plan pendant que votre thread continue de s’exécuter. Lorsque la séquence est terminée, elle est automatiquement répétée.

Si le contrôle d’animation a `ACS_CENTER` le style, le clip AVI est centré dans le contrôle et la taille du contrôle ne change pas. Si le contrôle d’animation n’a pas `ACS_CENTER` le style, le contrôle est redimensionné lors de l’ouverture du clip AVI à la taille des images dans le clip avi. La position du coin supérieur gauche du contrôle ne change pas, seule la taille du contrôle.

Si le contrôle d’animation a `ACS_TRANSPARENT` le style, le premier frame est dessiné à l’aide d’un arrière-plan transparent plutôt que de la couleur d’arrière-plan spécifiée dans le clip d’animation.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CAnimateCtrl :: CAnimateCtrl](#canimatectrl).

##  <a name="play"></a>  CAnimateCtrl::Play

Appelez cette fonction pour lire un clip AVI dans un contrôle d’animation.

```
BOOL Play(
    UINT nFrom,
    UINT nTo,
    UINT nRep);
```

### <a name="parameters"></a>Paramètres

*nFrom*<br/>
Index de base zéro du frame dans lequel la fonction commence. La valeur doit être inférieure à 65 536. La valeur 0 signifie que commence par la première image du clip AVI.

*nTo*<br/>
Index de base zéro de la trame dans laquelle la diffusion se termine. La valeur doit être inférieure à 65 536. La valeur-1 signifie qu’elle se termine par la dernière image du clip AVI.

*nRep*<br/>
Nombre de relectures du clip AVI. La valeur-1 signifie relire le fichier indéfiniment.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Le contrôle animation lira le clip en arrière-plan pendant que votre thread continue de s’exécuter. Si le contrôle d’animation `ACS_TRANSPARENT` a le style, le clip AVI est lu à l’aide d’un arrière-plan transparent plutôt que de la couleur d’arrière-plan spécifiée dans le clip d’animation.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CAnimateCtrl :: CAnimateCtrl](#canimatectrl).

##  <a name="seek"></a>  CAnimateCtrl::Seek

Appelez cette fonction pour afficher de manière statique une image unique de votre clip AVI.

```
BOOL Seek(UINT nTo);
```

### <a name="parameters"></a>Paramètres

*nTo*<br/>
Index de base zéro du frame à afficher. La valeur doit être inférieure à 65 536. La valeur 0 signifie que affiche la première image du clip AVI. La valeur-1 signifie que affiche la dernière image du clip AVI.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Si le contrôle d’animation `ACS_TRANSPARENT` a le style, le clip AVI est dessiné à l’aide d’un arrière-plan transparent plutôt que de la couleur d’arrière-plan spécifiée dans le clip d’animation.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAnimateCtrl :: CAnimateCtrl](#canimatectrl).

##  <a name="stop"></a>  CAnimateCtrl::Stop

Appelez cette fonction pour arrêter la diffusion d’un clip AVI dans un contrôle d’animation.

```
BOOL Stop();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CAnimateCtrl :: CAnimateCtrl](#canimatectrl).

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CAnimateCtrl::Create](#create)<br/>
[ON_CONTROL](message-map-macros-mfc.md#on_control)
