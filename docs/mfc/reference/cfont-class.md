---
title: CFont (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFont
- AFXWIN/CFont
- AFXWIN/CFont::CFont
- AFXWIN/CFont::CreateFont
- AFXWIN/CFont::CreateFontIndirect
- AFXWIN/CFont::CreatePointFont
- AFXWIN/CFont::CreatePointFontIndirect
- AFXWIN/CFont::FromHandle
- AFXWIN/CFont::GetLogFont
dev_langs:
- C++
helpviewer_keywords:
- CFont [MFC], CFont
- CFont [MFC], CreateFont
- CFont [MFC], CreateFontIndirect
- CFont [MFC], CreatePointFont
- CFont [MFC], CreatePointFontIndirect
- CFont [MFC], FromHandle
- CFont [MFC], GetLogFont
ms.assetid: 3fad6bfe-d6ce-4ab9-967a-5ce0aa102800
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c26cf70ad52037b4ebe88b983e6d9a91273897cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369666"
---
# <a name="cfont-class"></a>CFont (classe)
Encapsule une police GDI (Graphics Device Interface) Windows et fournit des fonctions membres pour la manipuler.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CFont : public CGdiObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CFont::CFont](#cfont)|Construit un objet `CFont`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CFont::CreateFont n'](#createfont)|Initialise un `CFont` avec les caractéristiques spécifiées.|  
|[CFont::CreateFontIndirect](#createfontindirect)|Initialise un `CFont` objet avec les caractéristiques donné dans un `LOGFONT` structure.|  
|[CFont::CreatePointFont](#createpointfont)|Initialise un `CFont` avec la hauteur spécifiée, mesurée en dixièmes de point et de police.|  
|[CFont::CreatePointFontIndirect](#createpointfontindirect)|Identique à `CreateFontIndirect` , sauf que la hauteur de police est mesurée en dixièmes d’un point au lieu des unités logiques.|  
|[CFont::FromHandle](#fromhandle)|Retourne un pointeur vers un `CFont` en fonction d’une fenêtre de l’objet **HFONT**.|  
|[CFont::GetLogFont](#getlogfont)|Remplit un `LOGFONT` avec des informations sur la police logique attachée à la `CFont` objet.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CFont::operator HFONT](#operator_hfont)|Retourne le handle de police GDI Windows attaché à la `CFont` objet.|  
  
## <a name="remarks"></a>Notes  
 Pour utiliser un `CFont` de l’objet, construisez un `CFont` de l’objet et attacher une police Windows à l’aide de [CreateFont](#createfont), [CreateFontIndirect](#createfontindirect), [CreatePointFont](#createpointfont), ou [CreatePointFontIndirect](#createpointfontindirect), puis utilisez les fonctions membres de l’objet pour manipuler la police.  
  
 Le `CreatePointFont` et `CreatePointFontIndirect` fonctions sont souvent plus faciles à utiliser que `CreateFont` ou `CreateFontIndirect` , car ils ne la conversion de la hauteur de la police à partir d’une taille de point sur les unités logiques automatiquement.  
  
 Pour plus d’informations sur `CFont`, consultez [objets graphiques](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CFont`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxwin.h  
  
##  <a name="cfont"></a>  CFont::CFont  
 Construit un objet `CFont`.  
  
```  
CFont();
```  
  
### <a name="remarks"></a>Notes  
 L’objet résultant doit être initialisée avec `CreateFont`, `CreateFontIndirect`, `CreatePointFont`, ou `CreatePointFontIndirect` avant de pouvoir être utilisé.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#70](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]  
  
##  <a name="createfont"></a>  CFont::CreateFont n'  
 Initialise un `CFont` objet avec les caractéristiques spécifiées.  
  
```  
BOOL CreateFont(
    int nHeight,  
    int nWidth,  
    int nEscapement,  
    int nOrientation,  
    int nWeight,  
    BYTE bItalic,  
    BYTE bUnderline,  
    BYTE cStrikeOut,  
    BYTE nCharSet,  
    BYTE nOutPrecision,  
    BYTE nClipPrecision,  
    BYTE nQuality,  
    BYTE nPitchAndFamily,  
    LPCTSTR lpszFacename);
```  
  
### <a name="parameters"></a>Paramètres  
 `nHeight`  
 Spécifie la hauteur souhaitée (en unités logiques) de la police. Consultez le `lfHeight` membre de la [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)structure dans le SDK Windows pour obtenir une description. La valeur absolue de `nHeight` ne doit pas dépasser 16 384 unités du périphérique après leur conversion. Pour toutes les comparaisons de hauteur, le mappeur de polices recherche la plus grande police qui ne dépasse pas la taille demandée ou la plus petite police si toutes les polices dépassent la taille demandée.  
  
 `nWidth`  
 Spécifie la largeur moyenne (en unités logiques) de caractères dans la police. Si `nWidth` est 0, les proportions de l’appareil doit concorder avec les proportions de numérisation des polices disponibles pour trouver la plus proche, déterminé par la valeur absolue de la différence.  
  
 `nEscapement`  
 Spécifie l’angle (en unités de degré de 0,1) entre le vecteur d’échappement et l’axe des abscisses de la surface d’affichage. Le vecteur d’échappement est la ligne à l’origine des premier et derniers caractères sur une ligne. L’angle est mesuré dans le sens inverse à partir de l’axe des abscisses. Consultez le `lfEscapement` membre dans le `LOGFONT` structure dans le SDK Windows pour plus d’informations.  
  
 `nOrientation`  
 Spécifie l’angle (en unités de degré de 0,1) entre la ligne de base d’un caractère et l’axe des abscisses. L’angle est mesuré dans le sens inverse à partir de l’axe des x pour les systèmes de coordonnées dans lequel l’axe y est bas et vers la droite de l’axe x pour les systèmes de coordonnées dans lequel l’axe y est activé.  
  
 `nWeight`  
 Spécifie l’épaisseur de police (en pixels ancrés par 1 000). Consultez le `lfWeight` membre dans le `LOGFONT` structure dans le SDK Windows pour plus d’informations. Les valeurs spécifiées sont approximatives ; l’apparence réelle dépend de la police. Certaines polices ont uniquement `FW_NORMAL`, `FW_REGULAR`, et `FW_BOLD` poids. Si `FW_DONTCARE` est spécifié, une pondération par défaut est utilisée.  
  
 `bItalic`  
 Spécifie si la police est en italique.  
  
 `bUnderline`  
 Spécifie si la police est soulignée.  
  
 `cStrikeOut`  
 Spécifie si les caractères de la police sont barrées. Spécifie une police barré, si une valeur différente de zéro.  
  
 `nCharSet`  
 Spécifie les setSee de caractère de la police la `lfCharSet` membre dans le `LOGFONT` structure dans le SDK Windows pour obtenir la liste de valeurs.  
  
 Le jeu de caractères OEM est dépendante du système.  
  
 Polices avec d’autres jeux de caractères peuvent exister dans le système. Une application qui utilise une police avec un jeu de caractères inconnu ne devez pas tenter de traduire ou l’interprétation des chaînes qui doivent être restitués avec cette police. Au lieu de cela, les chaînes doivent être passés directement au pilote de périphérique de sortie.  
  
 Le mappeur de polices n’utilise pas le `DEFAULT_CHARSET` valeur. Une application peut utiliser cette valeur pour permettre au nom et la taille de la police pour décrire complètement la police logique. Si une police portant le nom spécifié n’existe pas, une police à partir de n’importe quel jeu de caractères peut être remplacée par la police spécifiée. Pour éviter des résultats inattendus, les applications doivent utiliser le `DEFAULT_CHARSET` valeur avec parcimonie.  
  
 `nOutPrecision`  
 Spécifie la précision de la sortie souhaitée. La précision de sortie définit le degré de parenté doit correspondre à la sortie de la police demandée hauteur, largeur, l’orientation de caractères, échappement et le pas. Consultez le `lfOutPrecision` membre dans le `LOGFONT` structure dans le SDK Windows pour obtenir la liste de valeurs et plus d’informations.  
  
 `nClipPrecision`  
 Spécifie la précision de l’extrait de votre choix. La précision de découpage définit comment découper des caractères qui sont partiellement en dehors de la zone de découpage. Consultez le `lfClipPrecision` membre dans le `LOGFONT` structure dans le SDK Windows pour obtenir la liste de valeurs.  
  
 Pour utiliser une police incorporée d’en lecture seule, une application doit spécifier `CLIP_ENCAPSULATE`.  
  
 Pour obtenir une rotation cohérente de périphérique, les polices TrueType et les polices vectorielles, une application peut utiliser l’opérateur OR pour combiner les `CLIP_LH_ANGLES` valeur avec les autres `nClipPrecision` valeurs. Si le `CLIP_LH_ANGLES` bit est défini, la rotation de toutes les polices dépend de l’orientation du système de coordonnées gauche ou droite. (Pour plus d’informations sur l’orientation des systèmes de coordonnées, consultez la description de le `nOrientation` paramètre.) Si `CLIP_LH_ANGLES` est ne pas définie, les polices de périphérique toujours faire pivoter à gauche, mais la rotation des autres polices dépend de l’orientation du système de coordonnées.  
  
 `nQuality`  
 Spécifie la qualité de sortie de la police, qui définit comment l’interface GDI doit essayer de faire correspondre les attributs de police logique à ceux d’une police physique réelle. Consultez le `lfQuality` membre dans le `LOGFONT` structure dans le SDK Windows pour obtenir la liste de valeurs.  
  
 `nPitchAndFamily`  
 Spécifie la hauteur et la famille de la police. Consultez le `lfPitchAndFamily` membre dans le `LOGFONT` structure dans le SDK Windows pour obtenir la liste de valeurs et plus d’informations.  
  
 `lpszFacename`  
 Un `CString` ou un pointeur vers une chaîne se terminant par null qui spécifie le nom de la police. La longueur de cette chaîne ne doit pas dépasser 30 caractères. Les fenêtres [EnumFontFamilies](http://msdn.microsoft.com/library/windows/desktop/dd162619) fonction peut être utilisée pour énumérer toutes les polices disponibles actuellement. Si `lpszFacename` est `NULL`, l’interface GDI utilise une police indépendant du périphérique.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 La police peut ensuite être sélectionnée comme la police pour n’importe quel contexte de périphérique.  
  
 Le `CreateFont` (fonction) ne crée pas une nouvelle police Windows GDI. Il sélectionne simplement la plus proche à partir de polices physiques disponibles pour l’interface GDI.  
  
 Applications peuvent utiliser les paramètres par défaut pour la plupart des paramètres lors de la création d’une police logique. Les paramètres qui doivent toujours des valeurs spécifiques sont `nHeight` et `lpszFacename`. Si `nHeight` et `lpszFacename` ne sont pas définies par l’application, la police logique qui est créée est dépendante de l’appareil.  
  
 Lorsque vous avez terminé avec le `CFont` objet créé par le `CreateFont` fonction, utilisez `CDC::SelectObject` pour sélectionner une autre police dans le contexte de périphérique, puis supprimez le `CFont` objet n’est plus nécessaire.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#71](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]  
  
##  <a name="createfontindirect"></a>  CFont::CreateFontIndirect  
 Initialise un `CFont` objet avec les caractéristiques donné dans un [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)structure.  
  
```  
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpLogFont`  
 Pointe vers un `LOGFONT` structure qui définit les caractéristiques de la police logique.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 La police peut ensuite être sélectionnée comme la police actuelle de n’importe quel appareil.  
  
 Cette police présente les caractéristiques spécifiées dans le [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) structure. Lorsque la police est activée à l’aide de la [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) fonction membre, le mappeur de police GDI essaie de correspondre à la police logique avec une police physique existante. Si le mappeur de polices ne parvient pas à trouver une correspondance exacte pour la police logique, il fournit une autre police dont les caractéristiques correspondent à autant de caractéristiques demandées que possible.  
  
 Lorsque vous n’avez plus besoin du `CFont` objet créé par le `CreateFontIndirect` fonction, utilisez `CDC::SelectObject` pour sélectionner une autre police dans le contexte de périphérique, puis supprimez le `CFont` objet n’est plus nécessaire.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#72](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]  
  
##  <a name="createpointfont"></a>  CFont::CreatePointFont  
 Cette fonction fournit un moyen simple de créer une police d’une police spécifiée et la taille en points.  
  
```  
BOOL CreatePointFont(
    int nPointSize,  
    LPCTSTR lpszFaceName,  
    CDC* pDC = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `nPointSize`  
 Hauteur de la police en dixièmes d’un point a demandé. (Par exemple, passer 120 pour demander une police de 12 points.)  
  
 `lpszFaceName`  
 Un `CString` ou un pointeur vers une chaîne se terminant par null qui spécifie le nom de la police. La longueur de cette chaîne ne doit pas dépasser 30 caractères. Les fenêtres **EnumFontFamilies** fonction peut être utilisée pour énumérer toutes les polices disponibles actuellement. Si `lpszFaceName` est **NULL**, l’interface GDI utilise une police indépendant du périphérique.  
  
 `pDC`  
 Pointeur vers le [CDC](../../mfc/reference/cdc-class.md) objet à être utilisée pour convertir la hauteur en `nPointSize` sur des unités logiques. Si **NULL**, un contexte de périphérique est utilisé pour la conversion.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro en cas de réussite, sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Il convertit automatiquement la hauteur en `nPointSize` sur des unités logiques à l’aide de la `CDC` objet pointé par `pDC`.  
  
 Lorsque vous avez terminé avec le `CFont` objet créé par le `CreatePointFont` de fonction, tout d’abord sélectionner la police hors du contexte de périphérique, puis supprimez le `CFont` objet.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#73](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]  
  
##  <a name="createpointfontindirect"></a>  CFont::CreatePointFontIndirect  
 Cette fonction est identique à [CreateFontIndirect](#createfontindirect) , sauf que la **lfHeight** membre de la `LOGFONT` est interprétée en dixièmes d’un unités point plutôt que des appareils.  
  
```  
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,  
    CDC* pDC = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpLogFont`  
 Pointe vers un [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) structure qui définit les caractéristiques de la police logique. Le **lfHeight** membre de la `LOGFONT` structure est mesurée en dixièmes d’un point au lieu des unités logiques. (Par exemple, **lfHeight** à 120 pour demander une police de 12 points.)  
  
 `pDC`  
 Pointeur vers le [CDC](../../mfc/reference/cdc-class.md) objet à être utilisée pour convertir la hauteur en **lfHeight** sur des unités logiques. Si **NULL**, un contexte de périphérique est utilisé pour la conversion.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro en cas de réussite, sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction convertit automatiquement la hauteur en **lfHeight** sur des unités logiques à l’aide de la `CDC` objet pointé par `pDC` avant de passer le `LOGFONT` structure une session sur Windows.  
  
 Lorsque vous avez terminé avec le `CFont` objet créé par le `CreatePointFontIndirect` de fonction, tout d’abord sélectionner la police hors du contexte de périphérique, puis supprimez le `CFont` objet.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#74](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]  
  
##  <a name="fromhandle"></a>  CFont::FromHandle  
 Retourne un pointeur vers un `CFont` de l’objet en fonction d’un **HFONT** handle vers un objet de police Windows GDI.  
  
```  
static CFont* PASCAL FromHandle(HFONT hFont);
```  
  
### <a name="parameters"></a>Paramètres  
 `hFont`  
 Un **HFONT** handle vers une police de Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un `CFont` objet en cas de réussite ; **NULL**.  
  
### <a name="remarks"></a>Notes  
 Si un `CFont` objet n’est pas déjà attaché au handle, un fichier temporaire `CFont` objet est créé et attaché. Ce fichier temporaire `CFont` objet est valide uniquement jusqu'à ce que la prochaine fois que l’application possède des temps d’inactivité dans la boucle d’événements, alors graphique temporaire tous les objets sont supprimés. Une autre façon d’autres termes est que l’objet temporaire est valide uniquement lors du traitement du message d’une fenêtre.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#75](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]  
  
##  <a name="getlogfont"></a>  CFont::GetLogFont  
 Appelez cette fonction pour récupérer une copie de la `LOGFONT` la structure de `CFont`.  
  
```  
int GetLogFont(LOGFONT* pLogFont);
```  
  
### <a name="parameters"></a>Paramètres  
 *pLogFont*  
 Pointeur vers le [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) structure pour recevoir des informations sur les police.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la fonction réussit, sinon 0.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#76](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]  
  
##  <a name="operator_hfont"></a>  CFont::operator HFONT  
 Utilisez cet opérateur pour obtenir le handle Windows GDI de la police attaché à la `CFont` objet.  
  
```  
operator HFONT() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle de l’objet de police Windows GDI attaché à `CFont` cas de réussite ; **NULL**.  
  
### <a name="remarks"></a>Notes  
 Dans la mesure où cet opérateur est automatiquement utilisé pour les conversions entre `CFont` à [polices et texte](http://msdn.microsoft.com/library/windows/desktop/dd144819), vous pouvez passer `CFont` objets aux fonctions qui attendent **HFONT**s.  
  
 Pour plus d’informations sur l’utilisation des objets graphiques, consultez [graphique objets](http://msdn.microsoft.com/library/windows/desktop/dd144962) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#77](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC HIERSVR](../../visual-cpp-samples.md)   
 [Classe de CGdiObject](../../mfc/reference/cgdiobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)



