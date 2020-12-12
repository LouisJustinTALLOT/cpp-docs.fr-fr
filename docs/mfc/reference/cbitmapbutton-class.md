---
description: 'En savoir plus sur : CBitmapButton, classe'
title: CBitmapButton, classe
ms.date: 11/04/2016
f1_keywords:
- CBitmapButton
- AFXEXT/CBitmapButton
- AFXEXT/CBitmapButton::CBitmapButton
- AFXEXT/CBitmapButton::AutoLoad
- AFXEXT/CBitmapButton::LoadBitmaps
- AFXEXT/CBitmapButton::SizeToContent
helpviewer_keywords:
- CBitmapButton [MFC], CBitmapButton
- CBitmapButton [MFC], AutoLoad
- CBitmapButton [MFC], LoadBitmaps
- CBitmapButton [MFC], SizeToContent
ms.assetid: 9ad6cb45-c3c4-4fb1-96d3-1fe3df7bbcfc
ms.openlocfilehash: 93d114dce87aba4643af427f3726a5ffab004b77
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122705"
---
# <a name="cbitmapbutton-class"></a>CBitmapButton, classe

Crée des contrôles de bouton de commande étiquetés avec des images bitmap au lieu de texte.

## <a name="syntax"></a>Syntaxe

```
class CBitmapButton : public CButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CBitmapButton :: CBitmapButton](#cbitmapbutton)|Construit un objet `CBitmapButton`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CBitmapButton :: autoload](#autoload)|Associe un bouton dans une boîte de dialogue à un objet de la `CBitmapButton` classe, charge le ou les bitmaps par nom et dimensionne le bouton pour l’adapter à la bitmap.|
|[CBitmapButton :: LoadBitmaps](#loadbitmaps)|Initialise l’objet en chargeant une ou plusieurs ressources bitmap nommées à partir du fichier de ressources de l’application et en joignant les bitmaps à l’objet.|
|[CBitmapButton :: SizeToContent](#sizetocontent)|Dimensionne le bouton pour qu’il s’adapte à l’image bitmap.|

## <a name="remarks"></a>Notes

`CBitmapButton` les objets contiennent jusqu’à quatre bitmaps, qui contiennent des images pour les différents États qu’un bouton peut supposer : haut (ou normal), vers le haut (ou sélectionné), focus et désactivé. Seule la première bitmap est requise ; les autres sont facultatifs.

Les images de bouton bitmap incluent la bordure autour de l’image, ainsi que l’image elle-même. La bordure joue généralement un rôle dans la représentation de l’état du bouton. Par exemple, l’image bitmap de l’État ciblé est généralement similaire à celle de l’État up, mais avec un rectangle en pointillés à partir de la bordure ou d’une ligne pleine épaisse à la bordure. L’image bitmap de l’état désactivé est généralement similaire à celle de l’État haut, mais elle présente un contraste plus faible (par exemple, une sélection de menu grisée ou grisée).

Ces images bitmap peuvent avoir n’importe quelle taille, mais toutes sont traitées comme s’il s’agissait de la même taille que l’image bitmap de l’État up.

Différentes applications demandent différentes combinaisons d’images bitmap :

|Haut|Descendre|Avec focus|Désactivé|Application|
|--------|----------|-------------|--------------|-----------------|
|×||||Bitmap|
|×|×|||Bouton sans style de WS_TABSTOP|
|×|×|×|×|Bouton de boîte de dialogue avec tous les États|
|×|×|×||Bouton de boîte de dialogue avec style de WS_TABSTOP|

Lorsque vous créez un contrôle de bouton bitmap, définissez le style de BS_OWNERDRAW pour spécifier que le bouton est owner-drawn. Windows envoie alors les messages WM_MEASUREITEM et WM_DRAWITEM pour le bouton. le Framework gère ces messages et gère l’apparence du bouton pour vous.

### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>Pour créer un contrôle de bouton bitmap dans la zone cliente d’une fenêtre

1. Créez-en une à quatre images bitmap pour le bouton.

1. Construisez l’objet [CBitmapButton](#cbitmapbutton) .

1. Appelez la fonction [Create](../../mfc/reference/cbutton-class.md#create) pour créer le contrôle bouton Windows et l’attacher à l' `CBitmapButton` objet.

1. Appelez la fonction membre [LoadBitmaps](#loadbitmaps) pour charger les ressources bitmap après la construction du bouton bitmap.

### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>Pour inclure un contrôle de bouton bitmap dans une boîte de dialogue

1. Créez-en une à quatre images bitmap pour le bouton.

1. Créez un modèle de boîte de dialogue avec un bouton owner-draw positionné à l’endroit où vous souhaitez insérer le bouton bitmap. La taille du bouton dans le modèle n’a pas d’importance.

1. Définissez la légende du bouton sur une valeur telle que « MYIMAGE » et définissez un symbole pour le bouton tel que IDC_MYIMAGE.

1. Dans le script de ressources de votre application, donnez à chacune des images créées pour le bouton un ID construit en ajoutant l’une des lettres « U », « D », « F » ou « X » (pour le haut, le haut, le focus et la désactivation) à la chaîne utilisée pour la légende de bouton à l’étape 3. Pour la légende du bouton « MYIMAGE », par exemple, les ID sont « MYIMAGEU », « MYIMAGED », « MYIMAGEF » et « MYIMAGEX ». Vous **devez** spécifier l’ID de vos bitmaps entre guillemets doubles. Dans le cas contraire, l’éditeur de ressources assignera un entier à la ressource et le système MFC échouera lors du chargement de l’image.

1. Dans la classe de boîte de dialogue de votre application (dérivée de `CDialog` ), ajoutez un `CBitmapButton` objet de membre.

1. Dans la `CDialog` routine [OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog) de l’objet, appelez la `CBitmapButton` fonction de [chargement](#autoload) automatique de l’objet, en utilisant comme paramètres l’ID de contrôle du bouton et le `CDialog` pointeur de l’objet **`this`** .

Si vous souhaitez gérer des messages de notification Windows, tels que des BN_CLICKED, envoyés par un contrôle de bouton bitmap à son parent (généralement une classe dérivée de `CDialog` ), ajoutez à l' `CDialog` objet dérivé de, une entrée de table des messages et une fonction membre du gestionnaire de messages pour chaque message. Les notifications envoyées par un `CBitmapButton` objet sont les mêmes que celles envoyées par un objet [CButton](../../mfc/reference/cbutton-class.md) .

La classe [CToolBar](../../mfc/reference/ctoolbar-class.md) adopte une approche différente des boutons bitmap.

Pour plus d’informations sur `CBitmapButton` , consultez [contrôles](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CBitmapButton`

## <a name="requirements"></a>Spécifications

**En-tête :** afxext. h

## <a name="cbitmapbuttonautoload"></a><a name="autoload"></a> CBitmapButton :: autoload

Associe un bouton dans une boîte de dialogue à un objet de la `CBitmapButton` classe, charge le ou les bitmaps par nom et dimensionne le bouton pour l’adapter à la bitmap.

```
BOOL AutoLoad(
    UINT nID,
    CWnd* pParent);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
ID de contrôle du bouton.

*pParent*<br/>
Pointeur vers l’objet qui possède le bouton.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez la `AutoLoad` fonction pour initialiser un bouton owner-draw dans une boîte de dialogue sous la forme d’un bouton bitmap. Les instructions relatives à l’utilisation de cette fonction se trouvent dans les notes de la `CBitmapButton` classe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#75](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]

## <a name="cbitmapbuttoncbitmapbutton"></a><a name="cbitmapbutton"></a> CBitmapButton :: CBitmapButton

Crée un objet `CBitmapButton`.

```
CBitmapButton();
```

### <a name="remarks"></a>Notes

Après avoir créé l' `CBitmapButton` objet C++, appelez [CButton :: Create](../../mfc/reference/cbutton-class.md#create) pour créer le contrôle bouton Windows et l’attacher à l' `CBitmapButton` objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#57](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]

## <a name="cbitmapbuttonloadbitmaps"></a><a name="loadbitmaps"></a> CBitmapButton :: LoadBitmaps

Utilisez cette fonction lorsque vous souhaitez charger des images bitmap identifiées par leurs noms de ressources ou numéros d’ID, ou lorsque vous ne pouvez pas utiliser la `AutoLoad` fonction car, par exemple, vous créez un bouton bitmap qui ne fait pas partie d’une boîte de dialogue.

```
BOOL LoadBitmaps(
    LPCTSTR lpszBitmapResource,
    LPCTSTR lpszBitmapResourceSel = NULL,
    LPCTSTR lpszBitmapResourceFocus = NULL,
    LPCTSTR lpszBitmapResourceDisabled = NULL);

BOOL LoadBitmaps(
    UINT nIDBitmapResource,
    UINT nIDBitmapResourceSel = 0,
    UINT nIDBitmapResourceFocus = 0,
    UINT nIDBitmapResourceDisabled = 0);
```

### <a name="parameters"></a>Paramètres

*lpszBitmapResource*<br/>
Pointe vers la chaîne terminée par le caractère null qui contient le nom de l’image bitmap pour l’état normal ou « up » d’un bouton bitmap. Obligatoire.

*lpszBitmapResourceSel*<br/>
Pointe vers la chaîne terminée par le caractère null qui contient le nom de l’image bitmap pour l’état sélectionné ou « enfoncé » d’un bouton bitmap. Peut être NULL.

*lpszBitmapResourceFocus*<br/>
Pointe vers la chaîne terminée par le caractère null qui contient le nom de l’image bitmap pour l’état du focus d’un bouton bitmap. Peut être NULL.

*lpszBitmapResourceDisabled*<br/>
Pointe vers la chaîne terminée par le caractère null qui contient le nom de l’image bitmap pour l’état désactivé d’un bouton bitmap. Peut être NULL.

*nIDBitmapResource*<br/>
Spécifie le numéro d’ID de ressource de la ressource bitmap pour l’état normal ou « haut » d’un bouton bitmap. Obligatoire.

*nIDBitmapResourceSel*<br/>
Spécifie le numéro d’ID de ressource de la ressource bitmap pour l’état sélectionné ou « enfoncé » d’un bouton bitmap. Peut être 0.

*nIDBitmapResourceFocus*<br/>
Spécifie le numéro d’ID de ressource de la ressource bitmap pour l’état du focus du bouton bitmap. Peut être 0.

*nIDBitmapResourceDisabled*<br/>
Spécifie le numéro d’ID de ressource de la ressource bitmap pour l’état désactivé d’un bouton bitmap. Peut être 0.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#58](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]

## <a name="cbitmapbuttonsizetocontent"></a><a name="sizetocontent"></a> CBitmapButton :: SizeToContent

Appelez cette fonction pour redimensionner un bouton bitmap à la taille de l’image bitmap.

```cpp
void SizeToContent();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#59](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[CButton, classe](../../mfc/reference/cbutton-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
