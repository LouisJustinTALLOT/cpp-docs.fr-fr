---
title: Classe CBitmapButton
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
ms.openlocfilehash: df21591dec1da5861125d7e9480fb9345aaad061
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752948"
---
# <a name="cbitmapbutton-class"></a>Classe CBitmapButton

Crée des contrôles de bouton de commande étiquetés avec des images bitmap au lieu de texte.

## <a name="syntax"></a>Syntaxe

```
class CBitmapButton : public CButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CBitmapButton::CBitmapButton](#cbitmapbutton)|Construit un objet `CBitmapButton`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CBitmapButton::AutoLoad](#autoload)|Associe un bouton dans une boîte de `CBitmapButton` dialogue avec un objet de la classe, charge le bitmap par son nom, et taille le bouton pour s’adapter à la bitmap.|
|[CBitmapButton::LoadBitmaps](#loadbitmaps)|Initialise l’objet en chargeant une ou plusieurs ressources de bitmap nommées à partir du fichier de ressources de l’application et en attachant les bitmaps à l’objet.|
|[CBitmapButton::SizeToContent](#sizetocontent)|Taille le bouton pour accueillir la bitmap.|

## <a name="remarks"></a>Notes

`CBitmapButton`les objets contiennent jusqu’à quatre bitmaps, qui contiennent des images pour les différents états qu’un bouton peut supposer : vers le haut (ou normal), vers le bas (ou sélectionné), concentré, et désactivé. Seule la première bitmap est nécessaire; les autres sont facultatifs.

Les images Bitmap-bouton incluent la bordure autour de l’image ainsi que l’image elle-même. La bordure joue généralement un rôle dans l’affichage de l’état du bouton. Par exemple, la bitmap pour l’état focalisé est généralement comme celle pour l’état vers le haut, mais avec un rectangle pointillé encastré de la frontière ou une ligne solide épaisse à la frontière. La bitmap pour l’état handicapé ressemble généralement à celui pour l’état vers le haut, mais a un contraste plus faible (comme une sélection de menu tamisée ou gris).

Ces bitmaps peuvent être de n’importe quelle taille, mais tous sont traités comme s’ils étaient de la même taille que la bitmap pour l’état haut.

Diverses applications exigent différentes combinaisons d’images bitmap :

|Haut|Bas|Avec focus|Désactivé|Application|
|--------|----------|-------------|--------------|-----------------|
|×||||Bitmap|
|×|×|||Bouton sans style WS_TABSTOP|
|×|×|×|×|Bouton de dialogue avec tous les états|
|×|×|×||Bouton de dialogue avec le style WS_TABSTOP|

Lors de la création d’un contrôle bitmap-bouton, définissez le style BS_OWNERDRAW pour spécifier que le bouton est tiré par le propriétaire. Cela provoque Windows d’envoyer les WM_MEASUREITEM et WM_DRAWITEM messages pour le bouton; le cadre gère ces messages et gère l’apparence du bouton pour vous.

### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>Pour créer un contrôle bitmap-bouton dans la zone client d’une fenêtre

1. Créez des images de une à quatre bitmap pour le bouton.

1. Construire l’objet [CBitmapButton.](#cbitmapbutton)

1. Appelez la fonction [Créer](../../mfc/reference/cbutton-class.md#create) pour créer le contrôle `CBitmapButton` du bouton Windows et l’attacher à l’objet.

1. Appelez la fonction membre [LoadBitmaps](#loadbitmaps) pour charger les ressources de bitmap après la construction du bouton bitmap.

### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>Pour inclure un contrôle bitmap-bouton dans une boîte de dialogue

1. Créez des images de une à quatre bitmap pour le bouton.

1. Créez un modèle de dialogue avec un bouton de tirage du propriétaire positionné là où vous voulez le bouton bitmap. La taille du bouton dans le modèle n’a pas d’importance.

1. Réglez la légende du bouton à une valeur telle que « MYIMAGE » et définissez un symbole pour le bouton tel que IDC_MYIMAGE.

1. Dans le script de ressource de votre application, donnez à chacune des images créées pour le bouton un ID construit en appending l’une des lettres "U", "D", "F," ou "X" (pour haut, vers le bas, concentré, et désactivé) à la chaîne utilisée pour la légende du bouton dans l’étape 3. Pour la légende du bouton « MYIMAGE », par exemple, les DIU seraient « MYIMAGEU », « MYIMAGED », « MYIMAGEF » et « MYIMAGEX ». Vous **devez** spécifier l’ID de vos bitmaps dans des citations doubles. Dans le cas contraire, l’éditeur de ressources attribuera un integer à la ressource et MFC échouera lors du chargement de l’image.

1. Dans la classe de dialogue de `CDialog`votre `CBitmapButton` application (dérivée de ), ajoutez un objet membre.

1. Dans `CDialog` la routine [OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog) de `CBitmapButton` l’objet, appelez la fonction [AutoLoad](#autoload) de l’objet, en utilisant comme paramètres l’ID de contrôle du bouton et l’objet `CDialog` de **ce** pointeur.

Si vous souhaitez gérer les messages de notification Windows, tels que BN_CLICKED, envoyés par un contrôle `CDialog`bitmap-bouton à son parent (généralement une classe dérivée de ), ajouter à l’objet `CDialog`dérivé une entrée de carte de message et la fonction de membre de message-gestionnaire pour chaque message. Les notifications envoyées par un `CBitmapButton` objet sont les mêmes que celles envoyées par un objet [CButton.](../../mfc/reference/cbutton-class.md)

La classe [CToolBar](../../mfc/reference/ctoolbar-class.md) adopte une approche différente des boutons bitmap.

Pour plus `CBitmapButton`d’informations sur , voir [Contrôles](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CBitmapButton`

## <a name="requirements"></a>Spécifications

**En-tête:** afxext.h

## <a name="cbitmapbuttonautoload"></a><a name="autoload"></a>CBitmapButton::AutoLoad

Associe un bouton dans une boîte de `CBitmapButton` dialogue avec un objet de la classe, charge le bitmap par son nom, et taille le bouton pour s’adapter à la bitmap.

```
BOOL AutoLoad(
    UINT nID,
    CWnd* pParent);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
L’ID de contrôle du bouton.

*pParent*<br/>
Pointeur vers l’objet qui possède le bouton.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `AutoLoad` la fonction pour initialiser un bouton de tirage du propriétaire dans une boîte de dialogue comme un bouton bitmap. Les instructions pour l’utilisation de `CBitmapButton` cette fonction sont dans les remarques pour la classe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#75](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]

## <a name="cbitmapbuttoncbitmapbutton"></a><a name="cbitmapbutton"></a>CBitmapButton::CBitmapButton

Crée un objet `CBitmapButton` .

```
CBitmapButton();
```

### <a name="remarks"></a>Notes

Après avoir créé `CBitmapButton` l’objet C, appelez [CButton : : Créez](../../mfc/reference/cbutton-class.md#create) pour `CBitmapButton` créer le contrôle du bouton Windows et attachez-le à l’objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#57](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]

## <a name="cbitmapbuttonloadbitmaps"></a><a name="loadbitmaps"></a>CBitmapButton::LoadBitmaps

Utilisez cette fonction lorsque vous souhaitez charger des images de bitmap identifiées `AutoLoad` par leurs noms de ressources ou numéros d’identification, ou lorsque vous ne pouvez pas utiliser la fonction parce que, par exemple, vous créez un bouton bitmap qui ne fait pas partie d’une boîte de dialogue.

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
Points à la chaîne non terminée qui contient le nom de la bitmap pour un bouton bitmap état normal ou "up". Obligatoire.

*lpszBitmapResourceSel*<br/>
Points à la chaîne non terminée qui contient le nom de la bitmap pour un bouton bitmap sélectionné ou "bas" état. Peut être NULL.

*lpszBitmapResourceFocus*<br/>
Points à la chaîne non terminée qui contient le nom de la bitmap pour l’état focalisé d’un bouton bitmap. Peut être NULL.

*lpszBitmapResourceDisabled*<br/>
Points à la chaîne non terminée qui contient le nom de la bitmap pour l’état désactivé d’un bouton bitmap. Peut être NULL.

*nIDBitmapResource (en)*<br/>
Specifie le numéro d’identification des ressources de la ressource de bitmap pour l’état normal ou « haut » d’un bouton bitmap. Obligatoire.

*nIDBitmapResourceSel*<br/>
Spécifie le numéro d’identification des ressources de la ressource bitmap pour un bouton bitmap sélectionné ou "bas" état. Peut-être 0.

*nIDBitmapResourceFocus*<br/>
Specifie le numéro d’identification des ressources de la ressource bitmap pour l’état focalisé d’un bouton bitmap. Peut-être 0.

*nIDBitmapResourceDisabled*<br/>
Specifie le numéro d’identification des ressources de la ressource de bitmap pour l’état désactivé d’un bouton bitmap. Peut-être 0.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#58](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]

## <a name="cbitmapbuttonsizetocontent"></a><a name="sizetocontent"></a>CBitmapButton::SizeToContent

Appelez cette fonction pour resize un bouton bitmap à la taille de la bitmap.

```cpp
void SizeToContent();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#59](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]

## <a name="see-also"></a>Voir aussi

[Échantillon MFC CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[Classe CButton](../../mfc/reference/cbutton-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
