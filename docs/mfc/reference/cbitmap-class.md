---
title: CBitmap (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CBitmap
- AFXWIN/CBitmap
- AFXWIN/CBitmap::CBitmap
- AFXWIN/CBitmap::CreateBitmap
- AFXWIN/CBitmap::CreateBitmapIndirect
- AFXWIN/CBitmap::CreateCompatibleBitmap
- AFXWIN/CBitmap::CreateDiscardableBitmap
- AFXWIN/CBitmap::FromHandle
- AFXWIN/CBitmap::GetBitmap
- AFXWIN/CBitmap::GetBitmapBits
- AFXWIN/CBitmap::GetBitmapDimension
- AFXWIN/CBitmap::LoadBitmap
- AFXWIN/CBitmap::LoadMappedBitmap
- AFXWIN/CBitmap::LoadOEMBitmap
- AFXWIN/CBitmap::SetBitmapBits
- AFXWIN/CBitmap::SetBitmapDimension
dev_langs:
- C++
helpviewer_keywords:
- CBitmap [MFC], CBitmap
- CBitmap [MFC], CreateBitmap
- CBitmap [MFC], CreateBitmapIndirect
- CBitmap [MFC], CreateCompatibleBitmap
- CBitmap [MFC], CreateDiscardableBitmap
- CBitmap [MFC], FromHandle
- CBitmap [MFC], GetBitmap
- CBitmap [MFC], GetBitmapBits
- CBitmap [MFC], GetBitmapDimension
- CBitmap [MFC], LoadBitmap
- CBitmap [MFC], LoadMappedBitmap
- CBitmap [MFC], LoadOEMBitmap
- CBitmap [MFC], SetBitmapBits
- CBitmap [MFC], SetBitmapDimension
ms.assetid: 3980616a-c59d-495a-86e6-62bd3889c84c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e5b931c7ad4b560ce247f78dcb126f9669bceb67
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355861"
---
# <a name="cbitmap-class"></a>CBitmap (classe)
Encapsule une bitmap GDI (Graphics Device Interface) Windows et fournit des fonctions membres pour la manipuler.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CBitmap : public CGdiObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CBitmap::CBitmap](#cbitmap)|Construit un objet `CBitmap`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CBitmap::CreateBitmap](#createbitmap)|Initialise l’objet avec une image bitmap de mémoire dépendante de l’appareil qui a une largeur spécifiée, la hauteur et le modèle binaire.|  
|[CBitmap::CreateBitmapIndirect](#createbitmapindirect)|Initialise l’objet avec une image bitmap avec la largeur, la hauteur et le modèle binaire (le cas échéant) dans un **BITMAP** structure.|  
|[CBitmap::CreateCompatibleBitmap](#createcompatiblebitmap)|Initialise l’objet avec une image bitmap afin qu’il soit compatible avec un périphérique spécifié.|  
|[CBitmap::CreateDiscardableBitmap](#creatediscardablebitmap)|Initialise l’objet avec une image bitmap pouvant être éliminée qui est compatible avec un périphérique spécifié.|  
|[CBitmap::FromHandle](#fromhandle)|Retourne un pointeur vers un `CBitmap` en fonction d’un handle Windows de l’objet `HBITMAP` bitmap.|  
|[CBitmap::GetBitmap](#getbitmap)|Remplit un **BITMAP** structure avec des informations sur l’image bitmap.|  
|[CBitmap::GetBitmapBits](#getbitmapbits)|Copie les bits de la bitmap spécifiée dans la mémoire tampon spécifiée.|  
|[CBitmap::GetBitmapDimension](#getbitmapdimension)|Retourne la largeur et la hauteur de l’image bitmap. La hauteur et la largeur sont supposées avoir été définie précédemment le [SetBitmapDimension](#setbitmapdimension) fonction membre.|  
|[CBitmap::LoadBitmap](#loadbitmap)|Initialise l’objet par le chargement d’une ressource bitmap nommée à partir du fichier exécutable de l’application et l’attachement de la bitmap à l’objet.|  
|[CBitmap::LoadMappedBitmap](#loadmappedbitmap)|Charge une image bitmap et mappe les couleurs les couleurs système en cours.|  
|[CBitmap::LoadOEMBitmap](#loadoembitmap)|Initialise l’objet par le chargement d’une bitmap Windows prédéfinie et l’attachement de la bitmap à l’objet.|  
|[CBitmap::SetBitmapBits](#setbitmapbits)|Définit les bits d’une image bitmap pour les valeurs de bits spécifié.|  
|[CBitmap::SetBitmapDimension](#setbitmapdimension)|Assigne une largeur et une hauteur à une image bitmap en unités de millimètre de 0,1.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CBitmap::operator HBITMAP](#operator_hbitmap)|Retourne le handle Windows associé à la `CBitmap` objet.|  
  
## <a name="remarks"></a>Notes  
 Pour utiliser un `CBitmap` de l’objet, construisez l’objet, attacher un handle de bitmap à l’aide d’une des fonctions membres d’initialisation et ensuite, appelez les fonctions membres de l’objet.  
  
 Pour plus d’informations sur l’utilisation des objets graphiques comme `CBitmap`, consultez [les objets de graphique](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CBitmap`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxwin.h  
  
##  <a name="cbitmap"></a>  CBitmap::CBitmap  
 Construit un objet `CBitmap`.  
  
```  
CBitmap();
```  
  
### <a name="remarks"></a>Notes  
 L’objet résultant doit être initialisée avec l’une des fonctions de membre de l’initialisation.  
  
##  <a name="createbitmap"></a>  CBitmap::CreateBitmap  
 Initialise une image bitmap de mémoire dépendante de l’appareil avec la largeur, la hauteur et le modèle binaire spécifiés.  
  
```  
BOOL CreateBitmap(
    int nWidth,  
    int nHeight,  
    UINT nPlanes,  
    UINT nBitcount,  
    const void* lpBits);
```  
  
### <a name="parameters"></a>Paramètres  
 `nWidth`  
 Spécifie la largeur (en pixels) de l’image bitmap.  
  
 `nHeight`  
 Spécifie la hauteur (en pixels) de l’image bitmap.  
  
 `nPlanes`  
 Spécifie le nombre de plans de couleur de l’image bitmap.  
  
 `nBitcount`  
 Spécifie le nombre de bits de couleur par pixel d’affichage.  
  
 `lpBits`  
 Pointe vers un tableau d’octets qui contient les valeurs de bit de l’image bitmap initiale. Si elle a la valeur **NULL**, la nouvelle image bitmap n’est pas initialisée.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Pour une image bitmap de couleur, le paramètre `nPlanes` ou `nBitcount` doit être défini avec la valeur 1. Si ces deux paramètres sont définis avec la valeur 1, `CreateBitmap` crée une image bitmap monochrome.  
  
 Bien qu’une image bitmap ne peut pas être directement sélectionnée pour un périphérique d’affichage, il peut être sélectionné en tant qu’image bitmap active pour un « contexte de périphérique de mémoire » à l’aide de [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) et copiés vers n’importe quel contexte de périphérique compatible à l’aide de la [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) (fonction).  
  
 Quand vous en avez terminé avec l’objet `CBitmap` créé par la fonction `CreateBitmap` , commencez par sélectionner l’image bitmap hors du contexte de périphérique, puis supprimez l’objet `CBitmap` .  
  
 Pour plus d’informations, consultez la description du champ **bmBits** de la structure **BITMAP** . Le [BITMAP](../../mfc/reference/bitmap-structure.md) structure est décrite sous la [CBitmap::CreateBitmapIndirect](#createbitmapindirect) fonction membre.  
  
##  <a name="createbitmapindirect"></a>  CBitmap::CreateBitmapIndirect  
 Initialise une image bitmap avec la largeur, la hauteur et le modèle binaire (le cas échéant) figurant à la structure vers laquelle pointe `lpBitmap`.  
  
```  
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpBitmap`  
 Pointe vers un [BITMAP](../../mfc/reference/bitmap-structure.md) structure qui contient des informations sur l’image bitmap.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Bien qu’une image bitmap ne peut pas être directement sélectionnée pour un périphérique d’affichage, il peut être sélectionné en tant qu’image bitmap active pour un contexte de périphérique de mémoire à l’aide de [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) et copiés vers n’importe quel contexte de périphérique compatible à l’aide de la [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) ou [CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) (fonction). (Le [CDC::PatBlt](../../mfc/reference/cdc-class.md#patblt) fonction pouvez copier l’image bitmap pour le pinceau actuel directement dans le contexte de périphérique d’affichage.)  
  
 Si le **BITMAP** structure vers laquelle pointe le `lpBitmap` paramètre a été renseigné à l’aide de la `GetObject` (fonction), les bits de l’image bitmap ne sont pas spécifiés, et l’image bitmap n’est pas initialisé. Pour initialiser l’image bitmap, une application peut utiliser une fonction comme [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) ou [SetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd162973) pour copier les bits du bitmap identifiée par le premier paramètre de `CGdiObject::GetObject` à l’image bitmap créé par `CreateBitmapIndirect`.  
  
 Lorsque vous avez terminé avec le `CBitmap` objet créé avec `CreateBitmapIndirect` de fonction, tout d’abord sélectionner l’image bitmap hors du contexte de périphérique, puis supprimez le `CBitmap` objet.  
  
##  <a name="createcompatiblebitmap"></a>  CBitmap::CreateCompatibleBitmap  
 Initialise une image bitmap qui est compatible avec le périphérique spécifié par `pDC`.  
  
```  
BOOL CreateCompatibleBitmap(
    CDC* pDC,  
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Paramètres  
 `pDC`  
 Spécifie le contexte de périphérique.  
  
 `nWidth`  
 Spécifie la largeur (en pixels) de l’image bitmap.  
  
 `nHeight`  
 Spécifie la hauteur (en pixels) de l’image bitmap.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 La bitmap a le même nombre de plans de couleur ou le même format de bits par pixel que le contexte de périphérique spécifié. Il peut être sélectionné en tant qu’image bitmap active pour n’importe quel appareil de mémoire qui est compatible avec celui spécifié par `pDC`.  
  
 Si `pDC` est un contexte de périphérique de mémoire, la bitmap retournée a le même format que l’image bitmap actuellement sélectionnée dans ce contexte de périphérique. Un « contexte de périphérique de mémoire » est un bloc de mémoire qui représente une surface d’affichage. Il peut être utilisé pour préparer des images en mémoire avant de les copier à la surface d’affichage du périphérique compatible.  
  
 Lors de la création d’un contexte de périphérique de mémoire, GDI sélectionne automatiquement un bitmap monochrome de stock pour celle-ci.  
  
 Comme un contexte de périphérique de mémoire de couleur peut avoir une couleur ou bitmap monochromes sélectionnés, le format de l’image bitmap retourné par la `CreateCompatibleBitmap` fonction n’est pas toujours le même ; Toutefois, le format d’une bitmap compatible pour un contexte de périphérique sans mémoire est toujours dans le format de l’appareil.  
  
 Lorsque vous avez terminé avec le `CBitmap` objet créé avec le `CreateCompatibleBitmap` de fonction, tout d’abord sélectionner l’image bitmap hors du contexte de périphérique, puis supprimez le `CBitmap` objet.  
  
##  <a name="creatediscardablebitmap"></a>  CBitmap::CreateDiscardableBitmap  
 Initialise une image bitmap pouvant être éliminée est compatible avec le contexte de périphérique identifié par `pDC`.  
  
```  
BOOL CreateDiscardableBitmap(
    CDC* pDC,  
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Paramètres  
 `pDC`  
 Spécifie un contexte de périphérique.  
  
 `nWidth`  
 Spécifie la largeur (en bits) de l’image bitmap.  
  
 `nHeight`  
 Spécifie la hauteur (en bits) de l’image bitmap.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 La bitmap a le même nombre de plans de couleur ou le même format de bits par pixel que le contexte de périphérique spécifié. Une application peut sélectionner cette image bitmap en tant qu’image bitmap active pour un périphérique de mémoire qui est compatible avec celui spécifié par `pDC`.  
  
 Windows peut ignorer une bitmap créée par cette fonction uniquement si une application ne le n'a pas sélectionné dans un contexte d’affichage. Si Windows ignore la bitmap lorsqu’il n’est pas sélectionnée et ultérieurement l’application tente de sélectionner, le [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) fonction retournera **NULL**.  
  
 Lorsque vous avez terminé avec le `CBitmap` objet créé avec le `CreateDiscardableBitmap` de fonction, tout d’abord sélectionner l’image bitmap hors du contexte de périphérique, puis supprimez le `CBitmap` objet.  
  
##  <a name="fromhandle"></a>  CBitmap::FromHandle  
 Retourne un pointeur vers un `CBitmap` lorsqu’un handle vers une bitmap GDI Windows de l’objet.  
  
```  
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>Paramètres  
 `hBitmap`  
 Spécifie une bitmap GDI de Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un `CBitmap` objet en cas de réussite ; **NULL**.  
  
### <a name="remarks"></a>Notes  
 Si un `CBitmap` objet n’est pas déjà attaché au handle, un fichier temporaire `CBitmap` objet est créé et attaché. Ce fichier temporaire `CBitmap` objet est valide uniquement jusqu'à ce que la prochaine fois que l’application possède des temps d’inactivité dans la boucle d’événements, alors graphique temporaire tous les objets sont supprimés. Une autre façon d’autres termes est que l’objet temporaire est valide uniquement lors du traitement du message d’une fenêtre.  
  
##  <a name="getbitmap"></a>  CBitmap::GetBitmap  
 Récupère les propriétés de l’image de l’image bitmap attaché.  
  
```  
int GetBitmap(BITMAP* pBitMap);
```  
  
### <a name="parameters"></a>Paramètres  
 `pBitMap`  
 Pointeur vers un [Structure BITMAP](../../mfc/reference/bitmap-structure.md) structure qui recevra les propriétés de l’image. Ce paramètre ne doit pas être `NULL`.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la méthode a réussi ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getbitmapbits"></a>  CBitmap::GetBitmapBits  
 Copie le modèle binaire de l’image bitmap jointe dans la mémoire tampon spécifiée.  
  
```  
DWORD GetBitmapBits(
    DWORD dwCount,  
    LPVOID lpBits) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `dwCount`  
 Nombre d’octets à copier dans la mémoire tampon.  
  
 `lpBits`  
 Pointeur vers la mémoire tampon qui reçoit l’image bitmap.  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’octets copiés dans la mémoire tampon si la méthode a réussi ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Utilisez [CBitmap::GetBitmap](#getbitmap) pour déterminer la taille de la mémoire tampon requise.  
  
##  <a name="getbitmapdimension"></a>  CBitmap::GetBitmapDimension  
 Retourne la largeur et la hauteur de l’image bitmap.  
  
```  
CSize GetBitmapDimension() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La largeur et la hauteur de l’image bitmap, mesurée en unités de millimètre de 0,1. La hauteur est dans le **cy** membre de la `CSize` objet et la largeur est dans le **cx** membre. Si la largeur du bitmap et la hauteur n’ont pas été définies à l’aide de `SetBitmapDimension`, la valeur de retour est 0.  
  
### <a name="remarks"></a>Notes  
 La hauteur et la largeur sont supposées avoir été définie précédemment à l’aide de la [SetBitmapDimension](#setbitmapdimension) fonction membre.  
  
##  <a name="loadbitmap"></a>  CBitmap::LoadBitmap  
 Charge la ressource bitmap nommée par `lpszResourceName` ou identifiée par le numéro d’ID dans `nIDResource` à partir du fichier exécutable de l’application.  
  
```  
BOOL LoadBitmap(LPCTSTR lpszResourceName);  
BOOL LoadBitmap(UINT nIDResource);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszResourceName`  
 Pointe vers une chaîne terminée par le caractère null qui contient le nom de la ressource bitmap.  
  
 `nIDResource`  
 Spécifie le numéro d’ID de ressource de la ressource bitmap.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 L’image bitmap chargé est attaché à la `CBitmap` objet.  
  
 Si l’image bitmap est identifié par `lpszResourceName` n’existe pas ou si la mémoire est insuffisante pour charger l’image bitmap, la fonction retourne 0.  
  
 Vous pouvez utiliser la [CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) fonction pour supprimer l’image bitmap est chargée par le `LoadBitmap` (fonction), ou le `CBitmap` destructeur supprime l’objet pour vous.  
  
> [!CAUTION]
>  Avant de supprimer l’objet, assurez-vous qu’il n’est pas sélectionnée dans un contexte de périphérique.  
  
 Les images suivantes ont été ajoutées à Windows 3.1 et versions ultérieures :  
  
 **OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI**  
  
 Ces bitmaps ne figurent pas dans les pilotes de périphérique pour les versions de Windows 3.0 et versions antérieures. Pour obtenir une liste complète des bitmaps et un affichage de leur apparition, consultez le Kit de développement logiciel Windows.  
  
##  <a name="loadmappedbitmap"></a>  CBitmap::LoadMappedBitmap  
 Appelez cette fonction membre pour charger une image bitmap et de mapper les couleurs pour les couleurs système en cours.  
  
```  
BOOL LoadMappedBitmap(
    UINT nIDBitmap,  
    UINT nFlags = 0,  
    LPCOLORMAP lpColorMap = NULL,  
    int nMapSize = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 `nIDBitmap`  
 L’ID de la ressource bitmap.  
  
 `nFlags`  
 Un indicateur pour une image bitmap. Peut être zéro ou **CMB_MASKED**.  
  
 `lpColorMap`  
 Un pointeur vers un **COLORMAP** structure qui contient les informations de couleur nécessaires pour mapper les bitmaps. Si ce paramètre est **NULL**, la fonction utilise la table des couleurs par défaut.  
  
 *nMapSize*  
 Le nombre de cartes en couleur pointée par `lpColorMap`.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Par défaut, `LoadMappedBitmap` mappera couleurs couramment utilisées dans les glyphes de bouton.  
  
 Pour plus d’informations sur la création d’une image bitmap mappée, consultez la fonction Windows [CreateMappedBitmap](http://go.microsoft.com/fwlink/p/?linkid=230562) et [COLORMAP](http://msdn.microsoft.com/library/windows/desktop/bb760448) structure dans le SDK Windows.  
  
##  <a name="loadoembitmap"></a>  CBitmap::LoadOEMBitmap  
 Charge une bitmap prédéfinie utilisée par Windows.  
  
```  
BOOL LoadOEMBitmap(UINT nIDBitmap);
```  
  
### <a name="parameters"></a>Paramètres  
 `nIDBitmap`  
 Numéro d’identification de la bitmap Windows prédéfinie. Les valeurs possibles sont répertoriées ci-dessous à partir de WINDOWS. H :  
  
|||  
|-|-|  
|**OBM_BTNCORNERS**|**OBM_OLD_RESTORE**|  
|**OBM_BTSIZE**|**OBM_OLD_RGARROW**|  
|**OBM_CHECK**|**OBM_OLD_UPARROW**|  
|**OBM_CHECKBOXES**|**OBM_OLD_ZOOM**|  
|**OBM_CLOSE**|**OBM_REDUCE**|  
|**OBM_COMBO**|**OBM_REDUCED**|  
|**OBM_DNARROW**|**OBM_RESTORE**|  
|**OBM_DNARROWD**|**OBM_RESTORED**|  
|**OBM_DNARROWI**|**OBM_RGARROW**|  
|**OBM_LFARROW**|**OBM_RGARROWD**|  
|**OBM_LFARROWD**|**OBM_RGARROWI**|  
|**OBM_LFARROWI**|**OBM_SIZE**|  
|**OBM_MNARROW**|**OBM_UPARROW**|  
|**OBM_OLD_CLOSE**|**OBM_UPARROWD**|  
|**OBM_OLD_DNARROW**|**OBM_UPARROW**|  
|**OBM_OLD_LFARROW**|**OBM_ZOOM**|  
|**OBM_OLD_REDUCE**|**OBM_ZOOMD**|  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Bitmap des noms qui commencent par **OBM_OLD** représentent les bitmaps utilisées par les versions de Windows antérieures à 3.0.  
  
 Notez que la constante **OEMRESOURCE** doit être défini avant l’inclusion de WINDOWS. H pour pouvoir utiliser le **OBM_** constantes.  
  
##  <a name="operator_hbitmap"></a>  CBitmap::operator HBITMAP  
 Utilisez cet opérateur pour obtenir le handle Windows GDI joint de le `CBitmap` objet.  
  
```  
operator HBITMAP() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Si réussie, un handle vers l’objet GDI Windows représenté par le `CBitmap` de l’objet ; sinon **NULL**.  
  
### <a name="remarks"></a>Notes  
 Cet opérateur est un opérateur de cast, qui prend en charge l’utilisation directe d’une `HBITMAP` objet.  
  
 Pour plus d’informations sur l’utilisation des objets graphiques, consultez [graphique objets](http://msdn.microsoft.com/library/windows/desktop/dd144962) dans le Kit de développement logiciel Windows.  
  
##  <a name="setbitmapbits"></a>  CBitmap::SetBitmapBits  
 Définit les bits d’une image bitmap pour les valeurs de bit données par `lpBits`.  
  
```  
DWORD SetBitmapBits(
    DWORD dwCount,  
    const void* lpBits);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwCount`  
 Spécifie le nombre d’octets indiqué par `lpBits`.  
  
 `lpBits`  
 Pointe vers le **octets** tableau qui contient les valeurs en pixels doit être copié vers le `CBitmap` objet. Dans l’ordre de l’image bitmap être en mesure d’afficher son image correctement, les valeurs doivent être formatés pour respecter les valeurs de profondeur de couleur, la largeur et la hauteur qui ont été spécifiés lors de la création de l’instance CBitmap. Pour plus d’informations, consultez [CBitmap::CreateBitmap](#createbitmap).  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’octets utilisés lors de la définition des bits de la bitmap ; 0 si la fonction échoue.  
  
##  <a name="setbitmapdimension"></a>  CBitmap::SetBitmapDimension  
 Assigne une largeur et une hauteur à une image bitmap en unités de millimètre de 0,1.  
  
```  
CSize SetBitmapDimension(
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Paramètres  
 `nWidth`  
 Spécifie la largeur de l’image bitmap (en unités de 0,1-millimètre).  
  
 `nHeight`  
 Spécifie la hauteur de l’image bitmap (en unités de 0,1-millimètre).  
  
### <a name="return-value"></a>Valeur de retour  
 Les dimensions de bitmap précédente. Hauteur est dans le **cy** variable membre de la `CSize` objet et la largeur est dans le **cx** variable membre.  
  
### <a name="remarks"></a>Notes  
 L’interface GDI n’utilise pas ces valeurs à l’exception de to les retourner lorsqu’une application appelle la [GetBitmapDimension](#getbitmapdimension) fonction membre.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC MDI](../../visual-cpp-samples.md)   
 [Classe de CGdiObject](../../mfc/reference/cgdiobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)

