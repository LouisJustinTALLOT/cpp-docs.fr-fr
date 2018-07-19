---
title: CBitmapButton, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CBitmapButton
- AFXEXT/CBitmapButton
- AFXEXT/CBitmapButton::CBitmapButton
- AFXEXT/CBitmapButton::AutoLoad
- AFXEXT/CBitmapButton::LoadBitmaps
- AFXEXT/CBitmapButton::SizeToContent
dev_langs:
- C++
helpviewer_keywords:
- CBitmapButton [MFC], CBitmapButton
- CBitmapButton [MFC], AutoLoad
- CBitmapButton [MFC], LoadBitmaps
- CBitmapButton [MFC], SizeToContent
ms.assetid: 9ad6cb45-c3c4-4fb1-96d3-1fe3df7bbcfc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ab7147e360d98eb054062b2c2e14ee0ef7febf91
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37339058"
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
|[CBitmapButton::CBitmapButton](#cbitmapbutton)|Construit un objet `CBitmapButton`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CBitmapButton::AutoLoad](#autoload)|Associe un bouton dans une boîte de dialogue avec un objet de la `CBitmapButton` classe, charge le bitmap(s) par nom les tailles et, le bouton pour s’ajuster à l’image bitmap.|  
|[CBitmapButton::LoadBitmaps](#loadbitmaps)|Initialise l’objet en chargeant une ou plusieurs ressources bitmap nommée à partir du fichier de ressources de l’application et en attachant les bitmaps à l’objet.|  
|[CBitmapButton::SizeToContent](#sizetocontent)|Redimensionne le bouton en fonction de l’image bitmap.|  
  
## <a name="remarks"></a>Notes  
 `CBitmapButton` les objets contiennent des bitmaps jusqu'à quatre, qui contiennent des images pour les différents États qu’un bouton peut supposer : fonctionnelle (ou normal), bas (ou sélectionné), concentrée et désactivé. Seule la première bitmap est obligatoire. les autres sont facultatifs.  
  
 Les images de boutons bitmap incluent la bordure autour de l’image, ainsi que l’image elle-même. La bordure joue généralement dans l’affichage de l’état du bouton. Par exemple, l’image bitmap de l’état ayant le focus est généralement tel que celui pour l’état opérationnel, mais avec une incrustation de rectangle en pointillé à partir de la bordure ou une ligne pleine épaisse à la frontière. L’image bitmap pour désactivé état généralement ressemble à celui pour relâchée, mais n’a plus faible contraste (par exemple, une sélection de menu estompé ou grisée).  
  
 Ces bitmaps peut être de n’importe quelle taille, mais toutes sont traitées comme s’il s’agissait de la même taille que l’image bitmap de l’état opérationnel.  
  
 Diverses applications exigent différentes combinaisons d’images bitmap :  
  
|Monter|Bas|Avec focus|Désactivé|Application|  
|--------|----------|-------------|--------------|-----------------|  
|×||||Bitmap|  
|×|×|||Bouton sans style WS_TABSTOP|  
|×|×|×|×|Bouton de la boîte de dialogue avec tous les États|  
|×|×|×||Bouton de la boîte de dialogue avec le style WS_TABSTOP|  
  
 Lorsque vous créez un contrôle de bouton de bitmap, définissez le style BS_OWNERDRAW pour spécifier que le bouton est owner-drawn. Cela entraîne Windows envoyer les messages WM_MEASUREITEM et WM_DRAWITEM pour le bouton ; le framework gère ces messages et gère l’apparence du bouton pour vous.  
  
### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>Pour créer un contrôle de bouton de la bitmap dans la zone cliente d’une fenêtre  
  
1.  Créer un à quatre images bitmap du bouton.  
  
2.  Construire la [CBitmapButton](#cbitmapbutton) objet.  
  
3.  Appelez le [créer](../../mfc/reference/cbutton-class.md#create) (fonction) pour créer le contrôle de bouton Windows et l’attacher à la `CBitmapButton` objet.  
  
4.  Appelez le [LoadBitmaps](#loadbitmaps) fonction membre pour charger les ressources bitmap, une fois que le bouton bitmap est construit.  
  
### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>Pour inclure un contrôle de bouton de la bitmap dans une boîte de dialogue  
  
1.  Créer un à quatre images bitmap du bouton.  
  
2.  Créer un modèle de boîte de dialogue avec un bouton en mode owner-draw positionné dans lequel vous souhaitez que le bouton de bitmap. La taille du bouton dans le modèle n’a pas d’importance.  
  
3.  Définir la légende du bouton à une valeur telle que « MYIMAGE » et définir un symbole pour le bouton telles que IDC_MYIMAGE.  
  
4.  Dans le script de ressources de votre application, attribuez à chacun des images créées pour le bouton, un ID construit en ajoutant une lettre « U », « D », « F », ou « X » (par, vers le bas, concentré et désactivé) pour la chaîne utilisée pour la légende du bouton dans l’étape 3. Pour la légende du bouton « MYIMAGE », par exemple, l’ID est « MYIMAGEU », « MYIMAGED », « MYIMAGEF » et « MYIMAGEX ». Vous **doit** spécifiez l’ID de vos bitmaps entre guillemets doubles. Dans le cas contraire, l’éditeur de ressources affecte un entier à la ressource et MFC échoue lors du chargement de l’image.  
  
5.  Dans la classe de boîte de dialogue de votre application (dérivée de `CDialog`), ajoutez un `CBitmapButton` objet membre.  
  
6.  Dans le `CDialog` l’objet [OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog) appel routine, le `CBitmapButton` l’objet [AutoLoad](#autoload) à l’aide en tant que paramètres ID de contrôle du bouton de la fonction et le `CDialog` l’objet**cela** pointeur.  
  
 Si vous souhaitez gérer les messages de notification de Windows, telles que BN_CLICKED, envoyé par un contrôle de bouton de la bitmap à son parent (généralement une classe dérivée de `CDialog`), ajouter à la `CDialog`-objet dérivée un membre d’entrée et de gestionnaire de messages de table des messages fonction pour chaque message. Les notifications envoyées par un `CBitmapButton` objet sont les mêmes que celles envoyées par un [CButton](../../mfc/reference/cbutton-class.md) objet.  
  
 La classe [CToolBar](../../mfc/reference/ctoolbar-class.md) adopte une approche différente pour les boutons de bitmap.  
  
 Pour plus d’informations sur `CBitmapButton`, consultez [contrôles](../../mfc/controls-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 `CBitmapButton`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxext.h  
  
##  <a name="autoload"></a>  CBitmapButton::AutoLoad  
 Associe un bouton dans une boîte de dialogue avec un objet de la `CBitmapButton` classe, charge le bitmap(s) par nom les tailles et, le bouton pour s’ajuster à l’image bitmap.  
  
```  
BOOL AutoLoad(
    UINT nID,  
    CWnd* pParent);
```  
  
### <a name="parameters"></a>Paramètres  
 *nID*  
 ID de contrôle. du bouton  
  
 *pParent*  
 Pointeur vers l’objet qui possède le bouton.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Utilisez le `AutoLoad` fonction pour initialiser un bouton en mode owner-draw dans une boîte de dialogue comme un bouton bitmap. Instructions pour l’utilisation de cette fonction se trouvent dans les notes relatives à la `CBitmapButton` classe.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCControlLadenDialog#75](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]  
  
##  <a name="cbitmapbutton"></a>  CBitmapButton::CBitmapButton  
 Crée un objet `CBitmapButton`.  
  
```  
CBitmapButton();
```  
  
### <a name="remarks"></a>Notes  
 Après avoir créé le C++ `CBitmapButton` de l’objet, appelez [CButton::Create](../../mfc/reference/cbutton-class.md#create) pour créer le contrôle de bouton Windows et l’attacher à la `CBitmapButton` objet.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCControlLadenDialog#57](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]  
  
##  <a name="loadbitmaps"></a>  CBitmapButton::LoadBitmaps  
 Utilisez cette fonction lorsque vous souhaitez charger des images bitmap identifiés par leurs noms de ressources ou les numéros d’identification, ou lorsque vous ne pouvez pas utiliser le `AutoLoad` car, par exemple, vous créez un bouton bitmap qui ne fait pas partie d’une boîte de dialogue de la fonction.  
  
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
 *lpszBitmapResource*  
 Pointe vers la chaîne se terminant par null qui contient le nom de l’image bitmap pour les normal d’un bouton bitmap ou « up » de l’état. Obligatoire.  
  
 *lpszBitmapResourceSel*  
 Pointe vers la chaîne se terminant par null qui contient le nom de l’image bitmap pour un bouton bitmap est sélectionné, ou « down » de l’état. Peut être NULL.  
  
 *lpszBitmapResourceFocus*  
 Pointe vers la chaîne se terminant par null qui contient le nom de l’image bitmap pour un bouton bitmap concentré état. Peut être NULL.  
  
 *lpszBitmapResourceDisabled*  
 Pointe vers la chaîne se terminant par null qui contient le nom de l’image bitmap pour un bouton bitmap l’état désactivé. Peut être NULL.  
  
 *nIDBitmapResource*  
 Spécifie le numéro d’ID de ressource de la ressource bitmap pour les normal d’un bouton bitmap ou « up » de l’état. Obligatoire.  
  
 *nIDBitmapResourceSel*  
 Spécifie le numéro d’ID de ressource de la ressource bitmap pour un bouton bitmap est sélectionné ou à l’état « inactif ». Peut être 0.  
  
 *nIDBitmapResourceFocus*  
 Spécifie le numéro d’ID de ressource de la ressource bitmap de l’état ayant le focus d’un bouton bitmap. Peut être 0.  
  
 *nIDBitmapResourceDisabled*  
 Spécifie le numéro d’ID de ressource de la ressource bitmap de l’état désactivé d’un bouton bitmap. Peut être 0.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCControlLadenDialog#58](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]  
  
##  <a name="sizetocontent"></a>  CBitmapButton::SizeToContent  
 Appelez cette fonction pour redimensionner un bouton bitmap à la taille de la bitmap.  
  
```  
void SizeToContent();
```  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCControlLadenDialog#59](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [CTRLTEST MFC, exemple](../../visual-cpp-samples.md)   
 [CButton, classe](../../mfc/reference/cbutton-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)

