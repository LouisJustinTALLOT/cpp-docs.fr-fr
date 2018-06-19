---
title: CPen (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPen
- AFXWIN/CPen
- AFXWIN/CPen::CPen
- AFXWIN/CPen::CreatePen
- AFXWIN/CPen::CreatePenIndirect
- AFXWIN/CPen::FromHandle
- AFXWIN/CPen::GetExtLogPen
- AFXWIN/CPen::GetLogPen
dev_langs:
- C++
helpviewer_keywords:
- CPen [MFC], CPen
- CPen [MFC], CreatePen
- CPen [MFC], CreatePenIndirect
- CPen [MFC], FromHandle
- CPen [MFC], GetExtLogPen
- CPen [MFC], GetLogPen
ms.assetid: 93175a3a-d46c-4768-be8d-863254f97a5f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 995e3f85ec21cae1be18f0bf7b6548c912ca5254
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376377"
---
# <a name="cpen-class"></a>CPen (classe)
Encapsule un stylet GDI (Graphics Device Interface) Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CPen : public CGdiObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CPen::CPen](#cpen)|Construit un objet `CPen`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CPen::CreatePen](#createpen)|Crée un stylet cosmétique ou géométrique logique avec le style spécifié, la largeur et le pinceau attributs et l’attache à le `CPen` objet.|  
|[CPen::CreatePenIndirect](#createpenindirect)|Crée un stylet avec le style, la largeur et la couleur donnée un [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041) de la structure et l’attache à le `CPen` objet.|  
|[CPen::FromHandle](#fromhandle)|Retourne un pointeur vers un `CPen` en fonction d’une fenêtre de l’objet `HPEN`.|  
|[CPen::GetExtLogPen](#getextlogpen)|Obtient un [EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711) structure sous-jacente.|  
|[CPen::GetLogPen](#getlogpen)|Obtient un [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041) structure sous-jacente.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CPen::operator HPEN](#operator_hpen)|Retourne le handle Windows associé à la `CPen` objet.|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur l’utilisation de `CPen`, consultez [objets graphiques](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CPen`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxwin.h  
  
##  <a name="cpen"></a>  CPen::CPen  
 Construit un objet `CPen`.  
  
```  
CPen();

 
CPen(
    int nPenStyle,  
    int nWidth,  
    COLORREF crColor);

 
CPen(
    int nPenStyle,  
    int nWidth,  
    const LOGBRUSH* pLogBrush,  
    int nStyleCount = 0,  
    const DWORD* lpStyle = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `nPenStyle`  
 Spécifie le style du stylet. Ce paramètre dans la première version du constructeur peut être une des valeurs suivantes :  
  
- **PS_SOLID** crée un stylet continu.  
  
- **PS_DASH** crée un stylet en pointillés. Valide uniquement lorsque la largeur du stylet est unités 1 ou moins, dans l’appareil.  
  
- **PS_DOT** crée un stylet en pointillés. Valide uniquement lorsque la largeur du stylet est unités 1 ou moins, dans l’appareil.  
  
- **PS_DASHDOT** crée un stylet avec des points et des tirets alternés. Valide uniquement lorsque la largeur du stylet est unités 1 ou moins, dans l’appareil.  
  
- **PS_DASHDOTDOT** crée un stylet avec deux points et des tirets alternés. Valide uniquement lorsque la largeur du stylet est unités 1 ou moins, dans l’appareil.  
  
- **PS_NULL** crée un stylet null.  
  
- **PS_INSIDEFRAME** crée un stylet qui dessine une ligne dans le cadre des formes fermées produites par les fonctions de sortie Windows GDI qui spécifient un rectangle englobant (par exemple, le **Ellipse**, **Rectangle** , `RoundRect`, `Pie`, et `Chord` fonctions membres). Lorsque ce style est utilisé avec les fonctions de sortie Windows GDI qui ne spécifient pas d’un rectangle englobant (par exemple, le `LineTo` fonction membre), la zone de dessin du stylet n’est pas limitée par un frame.  
  
 La deuxième version de la `CPen` constructeur spécifie une combinaison de type, le style, extrémité de fin et les attributs de jointure. Les valeurs de chaque catégorie doivent être combinées à l’aide de l’opérateur OR au niveau du bit (&#124;). Le type du stylet peut être une des valeurs suivantes :  
  
- **PS_GEOMETRIC** crée un stylet géométrique.  
  
- **PS_COSMETIC** crée un stylet.  
  
     La deuxième version de la `CPen` constructeur ajoute les styles suivants de stylet pour `nPenStyle`:  
  
- **PS_ALTERNATE** crée un stylet qui définit tous les autres pixels. (Ce style est applicable uniquement pour les stylets cosmétiques.)  
  
- **PS_USERSTYLE** crée un stylet qui utilise un tableau de style fourni par l’utilisateur.  
  
     L’extrémité de fin peut être une des valeurs suivantes :  
  
- **PS_ENDCAP_ROUND** majuscules sont arrondis.  
  
- **PS_ENDCAP_SQUARE** majuscules sont carrés.  
  
- **PS_ENDCAP_FLAT** majuscules sont fixes.  
  
     La jointure peut être une des valeurs suivantes :  
  
- **PS_JOIN_BEVEL** jointures sont en relief.  
  
- **PS_JOIN_MITER** jointures sont entre elles forment lorsqu’ils se trouvent dans la limite actuelle définie par le [SetMiterLimit](http://msdn.microsoft.com/library/windows/desktop/dd145076) (fonction). Si la jointure dépasse cette limite, il est en relief.  
  
- **PS_JOIN_ROUND** jointures sont arrondis.  
  
 `nWidth`  
 Spécifie la largeur du stylet.  
  
-   Pour la première version du constructeur, si cette valeur est 0, la largeur en unités de périphérique est toujours 1 pixel, quel que soit le mode de mappage.  
  
-   Pour la deuxième version du constructeur si `nPenStyle` est **PS_GEOMETRIC**, la largeur est exprimée en unités logiques. Si `nPenStyle` est **PS_COSMETIC**, la largeur doit être définie sur 1.  
  
 `crColor`  
 Contient une couleur RVB pour le stylet.  
  
 `pLogBrush`  
 Pointe vers un `LOGBRUSH` structure. Si `nPenStyle` est **PS_COSMETIC**, le `lbColor` membre de la `LOGBRUSH` structure spécifie la couleur du stylet et la `lbStyle` membre de la `LOGBRUSH` structure doit être définie sur **BS_ SOLIDE**. Si `nPenStyle` est **PS_GEOMETRIC**, tous les membres doivent être utilisées pour spécifier les attributs de pinceau du stylet.  
  
 `nStyleCount`  
 Spécifie la longueur, en unités de mot double de la `lpStyle` tableau. Cette valeur doit être égal à zéro si `nPenStyle` n’est pas **PS_USERSTYLE**.  
  
 `lpStyle`  
 Pointe vers un tableau de valeurs de mot double. La première valeur spécifie la longueur de la première ligne dans un style défini par l’utilisateur, la deuxième valeur spécifie la longueur de la première espace et ainsi de suite. Ce pointeur doit être **NULL** si `nPenStyle` n’est pas **PS_USERSTYLE**.  
  
### <a name="remarks"></a>Notes  
 Si vous utilisez le constructeur sans arguments, vous devez initialiser résultant `CPen` de l’objet avec la `CreatePen`, `CreatePenIndirect`, ou `CreateStockObject` fonctions membres.  
  
 Si vous utilisez le constructeur qui accepte des arguments, aucune initialisation supplémentaire n’est nécessaire. Le constructeur avec des arguments peut lever une exception si des erreurs sont rencontrées, alors que le constructeur sans arguments réussit toujours.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#99](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]  
  
##  <a name="createpen"></a>  CPen::CreatePen  
 Crée un stylet cosmétique ou géométrique logique avec le style spécifié, la largeur et le pinceau attributs et l’attache à le `CPen` objet.  
  
```  
BOOL CreatePen(
    int nPenStyle,  
    int nWidth,  
    COLORREF crColor);

 
BOOL CreatePen(
    int nPenStyle,  
    int nWidth,  
    const LOGBRUSH* pLogBrush,  
    int nStyleCount = 0,  
    const DWORD* lpStyle = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `nPenStyle`  
 Spécifie le style pour le stylet. Pour obtenir la liste des valeurs possibles, consultez la `nPenStyle` paramètre dans le [CPen](#cpen) constructeur.  
  
 `nWidth`  
 Spécifie la largeur du stylet.  
  
-   Pour la première version de `CreatePen`, si cette valeur est 0, la largeur en unités de périphérique est toujours 1 pixel, quel que soit le mode de mappage.  
  
-   Pour la deuxième version de `CreatePen`si `nPenStyle` est **PS_GEOMETRIC**, la largeur est exprimée en unités logiques. Si `nPenStyle` est **PS_COSMETIC**, la largeur doit être définie sur 1.  
  
 `crColor`  
 Contient une couleur RVB pour le stylet.  
  
 `pLogBrush`  
 Pointe vers un [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) structure. Si `nPenStyle` est **PS_COSMETIC**, le **lbColor** membre de la `LOGBRUSH` structure spécifie la couleur du stylet et la `lbStyle` membre de la `LOGBRUSH` structure doit être la valeur **BS_SOLID**. Si **nPenStyle** est **PS_GEOMETRIC**, tous les membres doivent être utilisées pour spécifier les attributs de pinceau du stylet.  
  
 `nStyleCount`  
 Spécifie la longueur, en unités de mot double de la `lpStyle` tableau. Cette valeur doit être égal à zéro si `nPenStyle` n’est pas **PS_USERSTYLE**.  
  
 `lpStyle`  
 Pointe vers un tableau de valeurs de mot double. La première valeur spécifie la longueur de la première ligne dans un style défini par l’utilisateur, la deuxième valeur spécifie la longueur de la première espace et ainsi de suite. Ce pointeur doit être **NULL** si `nPenStyle` n’est pas **PS_USERSTYLE**.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro en cas de réussite, ou zéro si la méthode échoue.  
  
### <a name="remarks"></a>Notes  
 La première version de `CreatePen` Initialise un stylet avec le style spécifié, la largeur et la couleur. Le stylet peut être sélectionné par la suite que le stylet actuel pour n’importe quel contexte de périphérique.  
  
 Stylets qui ont une largeur supérieure à 1 pixel doit toujours avoir le **PS_NULL**, **PS_SOLID**, ou **PS_INSIDEFRAME** style.  
  
 Si le stylet a la **PS_INSIDEFRAME** style et une couleur qui ne correspond pas à une couleur de la table logique, le stylet est dessiné avec une couleur dégradée. Le **PS_SOLID** style de stylet ne peut pas être utilisé pour créer un stylet avec une couleur dégradée. Le style **PS_INSIDEFRAME** est identique à **PS_SOLID** si la largeur du stylet est inférieure ou égale à 1.  
  
 La deuxième version de `CreatePen` Initialise un stylet logique cosmétique ou géométrique qui est spécifiés, de largeur, style et attributs de forme. La largeur d’un stylet est toujours 1 ; la largeur d’un stylet géométrique est toujours spécifiée en unités universelles. Une fois une application crée un stylet logique, elle peut sélectionner ce stylet dans un contexte de périphérique en appelant le [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) (fonction). Une fois un stylet est activée dans un contexte de périphérique, il peut être utilisé pour dessiner des lignes et des courbes.  
  
-   Si `nPenStyle` est **PS_COSMETIC** et **PS_USERSTYLE**, les entrées dans le `lpStyle` tableau spécifie les longueurs des tirets et des espaces dans les unités de style. Une unité de style est définie par le périphérique dans lequel le stylet est utilisé pour dessiner une ligne.  
  
-   Si `nPenStyle` est **PS_GEOMETRIC** et **PS_USERSTYLE**, les entrées dans le `lpStyle` tableau spécifie les longueurs des tirets et des espaces dans les unités logiques.  
  
-   Si `nPenStyle` est **PS_ALTERNATE**, l’unité de style est ignorée et tous les autres pixels est définie.  
  
 Lorsqu’une application ne requiert plus un stylet donné, il doit appeler la [CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) membre de fonction ou de détruire le `CPen` afin de la ressource n’est plus en cours d’utilisation de l’objet. Une application ne doit pas supprimer un stylet lorsque le stylet est sélectionné dans un contexte de périphérique.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#100](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]  
  
##  <a name="createpenindirect"></a>  CPen::CreatePenIndirect  
 Initialise un stylet qui a le style, la largeur et la couleur indiquée dans la structure vers laquelle pointe `lpLogPen`.  
  
```  
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpLogPen`  
 Pointe vers les fenêtres [LOGPEN](../../mfc/reference/logpen-structure.md) structure qui contient des informations sur le stylet.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur différente de zéro si la fonction réussit ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Stylets qui ont une largeur supérieure à 1 pixel doit toujours avoir le **PS_NULL**, **PS_SOLID**, ou **PS_INSIDEFRAME** style.  
  
 Si le stylet a la **PS_INSIDEFRAME** style et une couleur qui ne correspond pas à une couleur de la table logique, le stylet est dessiné avec une couleur dégradée. Le **PS_INSIDEFRAME** style est identique à **PS_SOLID** si la largeur du stylet est inférieure ou égale à 1.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#101](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]  
  
##  <a name="fromhandle"></a>  CPen::FromHandle  
 Retourne un pointeur vers un `CPen` objet en fonction d’un handle à un objet de stylet GDI de Windows.  
  
```  
static CPen* PASCAL FromHandle(HPEN hPen);
```  
  
### <a name="parameters"></a>Paramètres  
 *hPen*  
 `HPEN` handle du stylet de Windows GDI.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un `CPen` objet en cas de réussite ; **NULL**.  
  
### <a name="remarks"></a>Notes  
 Si aucun objet `CPen` n'est attaché au handle, un objet `CPen` temporaire est créé et attaché. Ce fichier temporaire `CPen` objet est valide uniquement jusqu'à ce que la prochaine fois que l’application possède des temps d’inactivité dans la boucle d’événements, alors graphique temporaire tous les objets sont supprimés. En d’autres termes, l’objet temporaire est uniquement valide pendant le traitement du message d’une fenêtre.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#105](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]  
  
##  <a name="getextlogpen"></a>  CPen::GetExtLogPen  
 Obtient un **EXTLOGPEN** structure sous-jacente.  
  
```  
int GetExtLogPen(EXTLOGPEN* pLogPen);
```  
  
### <a name="parameters"></a>Paramètres  
 `pLogPen`  
 Pointe vers une [EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711) structure qui contient des informations sur le stylet.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Le **EXTLOGPEN** structure définit le style, la largeur et le pinceau des attributs d’un stylet. Par exemple, appelez `GetExtLogPen` pour faire correspondre le style particulier d’un stylet.  
  
 Consultez les rubriques suivantes dans le SDK Windows pour plus d’informations sur les attributs de stylet :  
  
- [Fonction GetObject](http://msdn.microsoft.com/library/windows/desktop/dd144904)  
  
- [EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711)  
  
- [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041)  
  
- [ExtCreatePen](http://msdn.microsoft.com/library/windows/desktop/dd162705)  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant montre l’appel `GetExtLogPen` pour récupérer les attributs d’un stylet et créer un nouveau stylet cosmétique avec la même couleur.  
  
 [!code-cpp[NVC_MFCDocView#102](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]  
  
##  <a name="getlogpen"></a>  CPen::GetLogPen  
 Obtient un `LOGPEN` structure sous-jacente.  
  
```  
int GetLogPen(LOGPEN* pLogPen);
```  
  
### <a name="parameters"></a>Paramètres  
 `pLogPen`  
 Pointe vers un [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041) structure pour contenir des informations sur le stylet.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Le `LOGPEN` structure définit le style, la couleur et le modèle d’un stylet.  
  
 Par exemple, appelez `GetLogPen` pour faire correspondre le type particulier de stylet.  
  
 Consultez les rubriques suivantes dans le SDK Windows pour plus d’informations sur les attributs de stylet :  
  
- [Fonction GetObject](http://msdn.microsoft.com/library/windows/desktop/dd144904)  
  
- [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041)  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant montre l’appel `GetLogPen` pour récupérer un caractère de stylet, puis créer un nouveau stylet solid avec la même couleur.  
  
 [!code-cpp[NVC_MFCDocView#103](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]  
  
##  <a name="operator_hpen"></a>  CPen::operator HPEN  
 Obtient le handle Windows GDI joint de le `CPen` objet.  
  
```  
operator HPEN() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Si réussie, un handle vers l’objet GDI Windows représenté par le `CPen` de l’objet ; sinon **NULL**.  
  
### <a name="remarks"></a>Notes  
 Cet opérateur est un opérateur de cast, qui prend en charge l’utilisation directe d’une `HPEN` objet.  
  
 Pour plus d’informations sur l’utilisation des objets graphiques, consultez l’article [graphique objets](http://msdn.microsoft.com/library/windows/desktop/dd144962) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#104](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CGdiObject](../../mfc/reference/cgdiobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CBrush, classe](../../mfc/reference/cbrush-class.md)
