---
title: CBrush (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CBrush
- AFXWIN/CBrush
- AFXWIN/CBrush::CBrush
- AFXWIN/CBrush::CreateBrushIndirect
- AFXWIN/CBrush::CreateDIBPatternBrush
- AFXWIN/CBrush::CreateHatchBrush
- AFXWIN/CBrush::CreatePatternBrush
- AFXWIN/CBrush::CreateSolidBrush
- AFXWIN/CBrush::CreateSysColorBrush
- AFXWIN/CBrush::FromHandle
- AFXWIN/CBrush::GetLogBrush
dev_langs:
- C++
helpviewer_keywords:
- CBrush [MFC], CBrush
- CBrush [MFC], CreateBrushIndirect
- CBrush [MFC], CreateDIBPatternBrush
- CBrush [MFC], CreateHatchBrush
- CBrush [MFC], CreatePatternBrush
- CBrush [MFC], CreateSolidBrush
- CBrush [MFC], CreateSysColorBrush
- CBrush [MFC], FromHandle
- CBrush [MFC], GetLogBrush
ms.assetid: e5ef2c62-dd95-4973-9090-f52f605900e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ffd5e43267ad6a5a462705f410cc1073161ecf0
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954102"
---
# <a name="cbrush-class"></a>CBrush (classe)
Encapsule un pinceau GDI (Graphics Device Interface) Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CBrush : public CGdiObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CBrush::CBrush](#cbrush)|Construit un objet `CBrush`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CBrush::CreateBrushIndirect](#createbrushindirect)|Initialise un pinceau avec le style, la couleur et le modèle spécifié dans un [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) structure.|  
|[CBrush::CreateDIBPatternBrush](#createdibpatternbrush)|Initialise un pinceau avec un modèle spécifié par une bitmap indépendante du périphérique (DIB).|  
|[CBrush::CreateHatchBrush](#createhatchbrush)|Initialise un pinceau avec le motif hachuré spécifié et la couleur.|  
|[CBrush::CreatePatternBrush](#createpatternbrush)|Initialise un pinceau avec un modèle spécifié par une image bitmap.|  
|[CBrush::CreateSolidBrush](#createsolidbrush)|Initialise un pinceau avec la couleur unie spécifiée.|  
|[CBrush::CreateSysColorBrush](#createsyscolorbrush)|Crée un pinceau qui est la couleur système par défaut.|  
|[CBrush::FromHandle](#fromhandle)|Retourne un pointeur vers un `CBrush` en fonction d’un handle Windows de l’objet `HBRUSH` objet.|  
|[CBrush::GetLogBrush](#getlogbrush)|Obtient un [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) structure.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CBrush::operator HBRUSH](#operator_hbrush)|Retourne le handle Windows associé à la `CBrush` objet.|  
  
## <a name="remarks"></a>Notes  
 À utiliser un `CBrush` de l’objet, construisez un `CBrush` de l’objet et le passer à une `CDC` fonction membre qui requiert un pinceau.  
  
 Pinceaux peut être plein, livrés, ou un motif.  
  
 Pour plus d’informations sur `CBrush`, consultez [objets graphiques](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CBrush`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxwin.h  
  
##  <a name="cbrush"></a>  CBrush::CBrush  
 Construit un objet `CBrush`.  
  
```  
CBrush(); 
CBrush(COLORREF crColor); 
CBrush(int nIndex, COLORREF crColor); 
explicit CBrush(CBitmap* pBitmap);
```  
  
### <a name="parameters"></a>Paramètres  
 *crColor*  
 Spécifie la couleur de premier plan du pinceau comme une couleur RVB. Si le pinceau est livré, ce paramètre spécifie la couleur des hachures.  
  
 *nIndex*  
 Spécifie le style de hachurage du pinceau. Il peut prendre l’une des valeurs suivantes :  
  
- `HS_BDIAGONAL` Hachage vers le bas (de gauche à droite) à 45 degrés  
  
- `HS_CROSS` Hachurage horizontal et vertical  
  
- `HS_DIAGCROSS` Hachage à 45 degrés  
  
- `HS_FDIAGONAL` Hachage vers le haut (de gauche à droite) à 45 degrés  
  
- `HS_HORIZONTAL` Hachurage horizontal  
  
- `HS_VERTICAL` Hachage vertical  
  
 *pBitmap*  
 Pointe vers un `CBitmap` objet qui spécifie une image bitmap avec laquelle le pinceau peint.  
  
### <a name="remarks"></a>Notes  
 `CBrush` possède quatre surchargée constructeurs. Le constructeur sans arguments construit non initialisé `CBrush` objet doit être initialisé avant de pouvoir être utilisé.  
  
 Si vous utilisez le constructeur sans arguments, vous devez initialiser résultant `CBrush` avec l’objet [CreateSolidBrush](#createsolidbrush), [CreateHatchBrush](#createhatchbrush), [CreateBrushIndirect](#createbrushindirect), [CreatePatternBrush](#createpatternbrush), ou [CreateDIBPatternBrush](#createdibpatternbrush). Si vous utilisez un des constructeurs qui prend des arguments, puis plus aucune initialisation est nécessaire. Les constructeurs avec des arguments peuvent lever une exception si des erreurs sont rencontrées, alors que le constructeur sans arguments réussit toujours.  
  
 Le constructeur avec un seul [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) paramètre construit un pinceau uni avec la couleur spécifiée. Spécifie une valeur RVB de la couleur et peut être construite avec le `RGB` macro dans WINDOWS. H.  
  
 Le constructeur avec deux paramètres construit un pinceau à hachures. Le *nIndex* paramètre spécifie l’index d’un motif hachuré. Le *crColor* paramètre spécifie la couleur.  
  
 Le constructeur avec un `CBitmap` paramètre construit un pinceau à motif. Le paramètre identifie une image bitmap. La bitmap est censée ont été créés à l’aide de [CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap::LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap), ou [ CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap). La taille minimale d’une image bitmap à utiliser dans un motif de remplissage est 8 x 8 pixels.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]  
  
##  <a name="createbrushindirect"></a>  CBrush::CreateBrushIndirect  
 Initialise un pinceau avec un style, la couleur et le modèle spécifié dans un [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) structure.  
  
```  
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpLogBrush*  
 Pointe vers un [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) structure qui contient des informations sur le pinceau.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur différente de zéro si la fonction réussit ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Le pinceau peut ensuite être sélectionné comme le pinceau actuel pour n’importe quel contexte de périphérique.  
  
 Un pinceau créé à l’aide d’une image bitmap monochrome (plan 1, 1 bits par pixel) est dessiné à l’aide de couleurs de texte et d’arrière-plan actuelles. Pixels représentés par un bit défini à 0 seront dessinés avec la couleur de texte actuelle. Pixels représentés par un bit défini à 1 seront dessinés avec la couleur d’arrière-plan actuelle.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]  
  
##  <a name="createdibpatternbrush"></a>  CBrush::CreateDIBPatternBrush  
 Initialise un pinceau avec le modèle spécifié par une bitmap indépendante du périphérique (DIB).  
  
```  
BOOL CreateDIBPatternBrush(
    HGLOBAL hPackedDIB,  
    UINT nUsage);

 
BOOL CreateDIBPatternBrush(
    const void* lpPackedDIB,  
    UINT nUsage);
```  
  
### <a name="parameters"></a>Paramètres  
 *hPackedDIB*  
 Identifie un objet de la mémoire globale contenant un bitmap d’indépendants du périphérique (DIB) compressé.  
  
 *nUsage*  
 Spécifie si le **[] de bmiColors** champs de la [BITMAPINFO](../../mfc/reference/bitmapinfo-structure.md) la structure de données (qui fait partie de la « DIB comprimées ») contiennent des explicite des valeurs RVB ou des index dans la palette logique actuellement réalisée. Le paramètre doit être une des valeurs suivantes :  
  
- **DIB_PAL_COLORS** la table des couleurs se compose d’un tableau d’index de 16 bits.  
  
- **DIB_RGB_COLORS** la table des couleurs contient des valeurs RVB littérales.  
  
 *lpPackedDIB*  
 Pointe vers un DIB compressé consistant en un `BITMAPINFO` structure immédiatement suivi d’un tableau d’octets définissant les pixels de l’image bitmap.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Le pinceau peut ensuite être sélectionné pour n’importe quel contexte de périphérique qui prend en charge les opérations raster.  
  
 Les deux versions diffèrent dans la façon dont vous gérez le fichier DIB :  
  
-   Dans la première version, pour obtenir un handle du fichier DIB vous appelez Windows `GlobalAlloc` fonction pour allouer un bloc de mémoire globale et remplissez la mémoire avec le fichier DIB compressé.  
  
-   Dans la deuxième version, il n’est pas nécessaire d’appeler `GlobalAlloc` pour allouer de la mémoire pour le fichier DIB compressé.  
  
 Un fichier DIB compressé se compose d’un `BITMAPINFO` immédiatement suivi d’un tableau d’octets qui définit les pixels de la bitmap de structure de données. Les images bitmap utilisées en tant que modèles de remplissage doivent être de 8 x 8 pixels. Si la bitmap est supérieure, Windows crée un motif de remplissage à l’aide uniquement les bits correspondant pour les 8 premières lignes et 8 colonnes de pixels dans le coin supérieur gauche de l’image bitmap.  
  
 Lorsqu’une application sélectionne une forme de motif de deux couleurs DIB dans un contexte de périphérique monochrome, Windows ignore les couleurs spécifiées dans le fichier DIB et affiche à la place le pinceau de modèle en utilisant les couleurs de texte et d’arrière-plan actuelles du contexte de périphérique. Pixels associés à la première couleur (à l’offset 0 dans la table des couleurs DIB) du fichier DIB sont affichées à l’aide de la couleur du texte. Pixels associés à la deuxième couleur (au décalage 1 dans la table des couleurs) sont affichés à l’aide de la couleur d’arrière-plan.  
  
 Pour plus d’informations sur l’utilisation des fonctions suivantes de Windows, consultez le Kit de développement logiciel Windows :  
  
- [CreateDIBPatternBrush](http://msdn.microsoft.com/library/windows/desktop/dd183492) (cette fonction est fournie uniquement pour la compatibilité avec les applications écrites pour les versions de Windows antérieures à 3.0 ; utilisez la `CreateDIBPatternBrushPt` fonction.)  
  
- [CreateDIBPatternBrushPt](http://msdn.microsoft.com/library/windows/desktop/dd183493) (cette fonction doit être utilisée pour les applications Win32).  
  
- [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574)  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]  
  
##  <a name="createhatchbrush"></a>  CBrush::CreateHatchBrush  
 Initialise un pinceau avec le motif hachuré spécifié et la couleur.  
  
```  
BOOL CreateHatchBrush(
    int nIndex,  
    COLORREF crColor);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIndex*  
 Spécifie le style de hachurage du pinceau. Il peut prendre l’une des valeurs suivantes :  
  
- `HS_BDIAGONAL` Hachage vers le bas (de gauche à droite) à 45 degrés  
  
- `HS_CROSS` Hachurage horizontal et vertical  
  
- `HS_DIAGCROSS` Hachage à 45 degrés  
  
- `HS_FDIAGONAL` Hachage vers le haut (de gauche à droite) à 45 degrés  
  
- `HS_HORIZONTAL` Hachurage horizontal  
  
- `HS_VERTICAL` Hachage vertical  
  
 *crColor*  
 Spécifie la couleur de premier plan du pinceau comme une couleur RVB (la couleur des hachures). Consultez [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) dans le SDK Windows pour plus d’informations.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Le pinceau peut ensuite être sélectionné comme le pinceau actuel pour n’importe quel contexte de périphérique.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]  
  
##  <a name="createpatternbrush"></a>  CBrush::CreatePatternBrush  
 Initialise un pinceau avec un modèle spécifié par une image bitmap.  
  
```  
BOOL CreatePatternBrush(CBitmap* pBitmap);
```  
  
### <a name="parameters"></a>Paramètres  
 *pBitmap*  
 Identifie une image bitmap.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Le pinceau peut ensuite être sélectionné pour n’importe quel contexte de périphérique qui prend en charge les opérations raster. L’image bitmap identifié par *pBitmap* est initialisé en général à l’aide de la [CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap :: LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap), ou [CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap) (fonction).  
  
 Les images bitmap utilisées en tant que modèles de remplissage doivent être de 8 x 8 pixels. Si la bitmap est supérieure, Windows n’utilise que les bits correspondant aux 8 premières lignes et colonnes de pixels dans le coin supérieur gauche de l’image bitmap.  
  
 Un pinceau de modèle peut être supprimé sans affecter la bitmap associée. Cela signifie que l’image bitmap peut servir à créer n’importe quel nombre de formes de motif.  
  
 Un pinceau créé à l’aide d’un bitmap monochrome (plan de 1 couleur, de 1 bit par pixel) est dessiné à l’aide de couleurs de texte et d’arrière-plan actuelles. Pixels représentés par un bit défini à 0 sont dessinés avec la couleur de texte actuelle. Pixels représentés par un bit défini à 1 sont dessinés avec la couleur d’arrière-plan actuelle.  
  
 Pour plus d’informations sur l’utilisation de [CreatePatternBrush](http://msdn.microsoft.com/library/windows/desktop/dd183508), Windows, consultez le Kit de développement.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]  
  
##  <a name="createsolidbrush"></a>  CBrush::CreateSolidBrush  
 Initialise un pinceau avec une couleur unie spécifiée.  
  
```  
BOOL CreateSolidBrush(COLORREF crColor);
```  
  
### <a name="parameters"></a>Paramètres  
 *crColor*  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) structure qui spécifie la couleur du pinceau. La couleur spécifie une valeur RVB et peut être construite avec la macro RVB dans WINDOWS. H.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Le pinceau peut ensuite être sélectionné comme le pinceau actuel pour n’importe quel contexte de périphérique.  
  
 Lorsqu’une application a terminé d’utiliser le pinceau créé par `CreateSolidBrush`, il doit sélectionner le pinceau hors du contexte de périphérique.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CBrush::CBrush](#cbrush).  
  
##  <a name="createsyscolorbrush"></a>  CBrush::CreateSysColorBrush  
 Initialise une couleur.  
  
```  
BOOL CreateSysColorBrush(int nIndex);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIndex*  
 Spécifie un index de couleur. Cette valeur correspond à la couleur utilisée pour peindre l’un des éléments de 21 fenêtre. Consultez [GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371) dans le SDK Windows pour obtenir la liste de valeurs.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Le pinceau peut ensuite être sélectionné comme le pinceau actuel pour n’importe quel contexte de périphérique.  
  
 Lorsqu’une application a terminé d’utiliser le pinceau créé par `CreateSysColorBrush`, il doit sélectionner le pinceau hors du contexte de périphérique.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]  
  
##  <a name="fromhandle"></a>  CBrush::FromHandle  
 Retourne un pointeur vers un `CBrush` en fonction d’un handle Windows de l’objet [HBRUSH](#operator_hbrush) objet.  
  
```  
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```  
  
### <a name="parameters"></a>Paramètres  
 *hBrush*  
 `HANDLE` un pinceau GDI de Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un `CBrush` objet en cas de réussite ; **NULL**.  
  
### <a name="remarks"></a>Notes  
 Si un `CBrush` objet n’est pas déjà attaché au handle, un fichier temporaire `CBrush` objet est créé et attaché. Ce fichier temporaire `CBrush` objet est valide uniquement jusqu'à la prochaine fois que l’application a des temps d’inactivité dans la boucle d’événements. À ce stade, tous les objets graphiques temporaires sont supprimés. En d’autres termes, l’objet temporaire est valide uniquement lors du traitement du message d’une fenêtre.  
  
 Pour plus d’informations sur l’utilisation des objets graphiques, consultez [graphique objets](http://msdn.microsoft.com/library/windows/desktop/dd144962) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CBrush::CBrush](#cbrush).  
  
##  <a name="getlogbrush"></a>  CBrush::GetLogBrush  
 Appelez cette fonction membre pour récupérer le `LOGBRUSH` structure.  
  
```  
int GetLogBrush(LOGBRUSH* pLogBrush);
```  
  
### <a name="parameters"></a>Paramètres  
 *pLogBrush*  
 Pointe vers un [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) structure qui contient des informations sur le pinceau.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la fonction réussit, et *pLogBrush* est un pointeur valid, la valeur de retour est le nombre d’octets stockés dans la mémoire tampon.  
  
 Si la fonction réussit, et *pLogBrush* est **NULL**, la valeur de retour est le nombre d’octets requis pour conserver les informations de la fonction stocke dans la mémoire tampon.  
  
 Si la fonction échoue, la valeur de retour est 0.  
  
### <a name="remarks"></a>Notes  
 Le `LOGBRUSH` structure définit le style, la couleur et le modèle d’un pinceau.  
  
 Par exemple, appelez `GetLogBrush` pour faire correspondre la couleur ou le motif d’une image bitmap.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]  
  
##  <a name="operator_hbrush"></a>  CBrush::operator HBRUSH  
 Utilisez cet opérateur pour obtenir le handle Windows GDI joint de le `CBrush` objet.  
  
```  
operator HBRUSH() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Si réussie, un handle vers l’objet GDI Windows représenté par le `CBrush` de l’objet ; sinon **NULL**.  
  
### <a name="remarks"></a>Notes  
 Cet opérateur est un opérateur de cast, qui prend en charge l’utilisation directe d’une `HBRUSH` objet.  
  
 Pour plus d’informations sur l’utilisation des objets graphiques, consultez [graphique objets](http://msdn.microsoft.com/library/windows/desktop/dd144962) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC PROPDLG](../../visual-cpp-samples.md)   
 [Classe de CGdiObject](../../mfc/reference/cgdiobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CBitmap (classe)](../../mfc/reference/cbitmap-class.md)   
 [CDC, classe](../../mfc/reference/cdc-class.md)
