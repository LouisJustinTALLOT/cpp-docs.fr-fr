---
title: CPen, classe
ms.date: 11/04/2016
f1_keywords:
- CPen
- AFXWIN/CPen
- AFXWIN/CPen::CPen
- AFXWIN/CPen::CreatePen
- AFXWIN/CPen::CreatePenIndirect
- AFXWIN/CPen::FromHandle
- AFXWIN/CPen::GetExtLogPen
- AFXWIN/CPen::GetLogPen
helpviewer_keywords:
- CPen [MFC], CPen
- CPen [MFC], CreatePen
- CPen [MFC], CreatePenIndirect
- CPen [MFC], FromHandle
- CPen [MFC], GetExtLogPen
- CPen [MFC], GetLogPen
ms.assetid: 93175a3a-d46c-4768-be8d-863254f97a5f
ms.openlocfilehash: 952d270acd47b5834a06b731f7875ea2efdd4695
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502952"
---
# <a name="cpen-class"></a>CPen, classe

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
|[CPen::CreatePen](#createpen)|Crée un stylet cosmétique ou géométrique logique avec le style, la largeur et les attributs de pinceau spécifiés, et l' `CPen` attache à l’objet.|
|[CPen::CreatePenIndirect](#createpenindirect)|Crée un stylet avec le style, la largeur et la couleur donnés dans une structure [logpen,](/windows/win32/api/wingdi/ns-wingdi-logpen) , et l’attache à `CPen` l’objet.|
|[CPen:: FromHandle](#fromhandle)|Retourne un pointeur vers un `CPen` objet lorsqu’un HPEN Windows est fourni.|
|[CPen::GetExtLogPen](#getextlogpen)|Obtient une structure sous-jacente [EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen) .|
|[CPen::GetLogPen](#getlogpen)|Obtient une structure sous-jacente [logpen,](/windows/win32/api/wingdi/ns-wingdi-logpen) .|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CPen:: Operator HPEN](#operator_hpen)|Retourne le handle Windows attaché à l' `CPen` objet.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur `CPen`l’utilisation de, consultez [objets graphiques](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPen`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="cpen"></a>CPen::CPen

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

*nPenStyle*<br/>
Spécifie le style de stylet. Ce paramètre dans la première version du constructeur peut prendre l’une des valeurs suivantes:

- PS_SOLID crée un stylet plein.

- PS_DASH crée un stylets en pointillés. Valide uniquement lorsque la largeur du stylet est inférieure ou égale à 1, en unités de périphérique.

- PS_DOT crée un stylet en pointillés. Valide uniquement lorsque la largeur du stylet est inférieure ou égale à 1, en unités de périphérique.

- PS_DASHDOT crée un stylet avec des tirets et des points en alternance. Valide uniquement lorsque la largeur du stylet est inférieure ou égale à 1, en unités de périphérique.

- PS_DASHDOTDOT crée un stylet avec des tirets et des points doubles en alternance. Valide uniquement lorsque la largeur du stylet est inférieure ou égale à 1, en unités de périphérique.

- PS_NULL crée un stylet null.

- PS_INSIDEFRAME crée un stylet qui dessine une ligne à l’intérieur du frame des formes fermées produites par les fonctions de sortie Windows GDI qui spécifient un rectangle englobant ( `RoundRect`par `Pie`exemple `Ellipse` `Rectangle`,,,, et `Chord`fonctions membres). Quand ce style est utilisé avec les fonctions de sortie Windows GDI qui ne spécifient pas de rectangle englobant (par `LineTo` exemple, la fonction membre), la zone de dessin du stylet n’est pas limitée par un cadre.

La deuxième version du `CPen` constructeur spécifie une combinaison d’attributs de type, de style, d’extrémité de fin et de jointure. Les valeurs de chaque catégorie doivent être combinées à l’aide de l’opérateur&#124;or au niveau du bit (). Le type de stylo peut prendre l’une des valeurs suivantes:

- PS_GEOMETRIC crée un stylet géométrique.

- PS_COSMETIC crée un stylet cosmétique.

   La deuxième version du `CPen` constructeur ajoute les styles de stylet suivants pour *nPenStyle*:

- PS_ALTERNATE crée un stylet qui définit tous les autres pixels. (Ce style s’applique uniquement aux plumes cosmétiques.)

- PS_USERSTYLE crée un stylet qui utilise un tableau de style fourni par l’utilisateur.

   L’extrémité de fin peut être l’une des valeurs suivantes:

- Les extrémités de fin PS_ENDCAP_ROUND sont arrondies.

- Les extrémités de la PS_ENDCAP_SQUARE sont carrées.

- Les extrémités de la PS_ENDCAP_FLAT sont plates.

   La jointure peut prendre l’une des valeurs suivantes:

- Les jointures PS_JOIN_BEVEL sont biseautées.

- Les jointures PS_JOIN_MITER sont mitres lorsqu’elles sont dans la limite actuelle définie par la fonction [SetMiterLimit](/windows/win32/api/wingdi/nf-wingdi-setmiterlimit) . Si la jointure dépasse cette limite, elle est biseautée.

- Les jointures PS_JOIN_ROUND sont arrondies.

*nWidth*<br/>
Spécifie la largeur du stylet.

- Pour la première version du constructeur, si cette valeur est égale à 0, la largeur en unités de périphérique est toujours de 1 pixel, quel que soit le mode de mappage.

- Pour la deuxième version du constructeur, si *nPenStyle* est PS_GEOMETRIC, la largeur est indiquée en unités logiques. Si *nPenStyle* est PS_COSMETIC, la largeur doit être définie sur 1.

*crColor*<br/>
Contient une couleur RVB pour le stylet.

*pLogBrush*<br/>
Pointe vers une `LOGBRUSH` structure. Si *nPenStyle* est PS_COSMETIC, le membre *lbColor* de la `LOGBRUSH` structure spécifie la couleur du stylet et le membre *lbStyle* de `LOGBRUSH` la structure doit avoir la valeur BS_SOLID. Si *nPenStyle* est PS_GEOMETRIC, tous les membres doivent être utilisés pour spécifier les attributs de pinceau du stylet.

*nStyleCount*<br/>
Spécifie la longueur, en unités de mot double, du tableau *lpStyle* . Cette valeur doit être égale à zéro si *nPenStyle* n’est pas PS_USERSTYLE.

*lpStyle*<br/>
Pointe vers un tableau de valeurs de mot double. La première valeur spécifie la longueur du premier tiret dans un style défini par l’utilisateur, la deuxième valeur spécifie la longueur du premier espace, et ainsi de suite. Ce pointeur doit avoir la valeur NULL si *nPenStyle* n’est pas PS_USERSTYLE.

### <a name="remarks"></a>Notes

Si vous utilisez le constructeur sans arguments, vous devez initialiser l’objet résultant `CPen` avec les `CreatePen`fonctions membres `CreatePenIndirect`, ou `CreateStockObject` .

Si vous utilisez le constructeur qui accepte des arguments, aucune initialisation supplémentaire n’est nécessaire. Le constructeur avec des arguments peut lever une exception si des erreurs sont rencontrées, tandis que le constructeur sans arguments échoue toujours.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#99](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]

##  <a name="createpen"></a>  CPen::CreatePen

Crée un stylet cosmétique ou géométrique logique avec le style, la largeur et les attributs de pinceau spécifiés, et l' `CPen` attache à l’objet.

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

*nPenStyle*<br/>
Spécifie le style du stylet. Pour obtenir la liste des valeurs possibles, consultez le paramètre *nPenStyle* dans le constructeur [CPen](#cpen) .

*nWidth*<br/>
Spécifie la largeur du stylet.

- Pour la première version de `CreatePen`, si cette valeur est égale à 0, la largeur en unités de périphérique est toujours de 1 pixel, quel que soit le mode de mappage.

- Pour la deuxième version de `CreatePen`, si *nPenStyle* est PS_GEOMETRIC, la largeur est indiquée en unités logiques. Si *nPenStyle* est PS_COSMETIC, la largeur doit être définie sur 1.

*crColor*<br/>
Contient une couleur RVB pour le stylet.

*pLogBrush*<br/>
Pointe vers une structure [logbrush,](/windows/win32/api/wingdi/ns-wingdi-logbrush) . Si *nPenStyle* est PS_COSMETIC, le `lbColor` membre de la `LOGBRUSH` structure spécifie la couleur du stylet et le membre *lbStyle* de `LOGBRUSH` la structure doit avoir la valeur BS_SOLID. Si nPenStyle est PS_GEOMETRIC, tous les membres doivent être utilisés pour spécifier les attributs de pinceau du stylet.

*nStyleCount*<br/>
Spécifie la longueur, en unités de mot double, du tableau *lpStyle* . Cette valeur doit être égale à zéro si *nPenStyle* n’est pas PS_USERSTYLE.

*lpStyle*<br/>
Pointe vers un tableau de valeurs de mot double. La première valeur spécifie la longueur du premier tiret dans un style défini par l’utilisateur, la deuxième valeur spécifie la longueur du premier espace, et ainsi de suite. Ce pointeur doit avoir la valeur NULL si *nPenStyle* n’est pas PS_USERSTYLE.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite, ou zéro si la méthode échoue.

### <a name="remarks"></a>Notes

La première version de `CreatePen` Initialise un stylet avec le style, la largeur et la couleur spécifiés. Le stylet peut ensuite être sélectionné comme stylet actuel pour tout contexte de périphérique.

Les stylets dont la largeur est supérieure à 1 pixel doivent toujours avoir le style PS_NULL, PS_SOLID ou PS_INSIDEFRAME.

Si un stylet a le style PS_INSIDEFRAME et une couleur qui ne correspond pas à une couleur de la table des couleurs logiques, le stylet est dessiné avec une couleur déplacée. Le style de stylet PS_SOLID ne peut pas être utilisé pour créer un stylet avec une couleur décolorée. Le style PS_INSIDEFRAME est identique à PS_SOLID si la largeur du stylet est inférieure ou égale à 1.

La deuxième version de `CreatePen` Initialise un stylet cosmétique ou géométrique logique qui a le style, la largeur et les attributs de pinceau spécifiés. La largeur d’un stylet cosmétique est toujours 1; la largeur d’un stylet géométrique est toujours spécifiée en unités universelles. Une fois qu’une application a créé un stylet logique, elle peut sélectionner ce stylet dans un contexte de périphérique en appelant la fonction [CDC:: SelectObject](../../mfc/reference/cdc-class.md#selectobject) . Une fois le stylet sélectionné dans un contexte de périphérique, il peut être utilisé pour dessiner des lignes et des courbes.

- Si *nPenStyle* est PS_COSMETIC et PS_USERSTYLE, les entrées du tableau *lpStyle* spécifient des longueurs de tirets et d’espaces dans les unités de style. Une unité de style est définie par l’appareil dans lequel le stylet est utilisé pour dessiner une ligne.

- Si *nPenStyle* est PS_GEOMETRIC et PS_USERSTYLE, les entrées du tableau *lpStyle* spécifient des longueurs de tirets et d’espaces en unités logiques.

- Si *nPenStyle* est PS_ALTERNATE, l’unité de style est ignorée et tous les autres pixels sont définis.

Quand une application n’a plus besoin d’un stylet donné, elle doit appeler la fonction membre [CGdiObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) ou détruire l' `CPen` objet afin que la ressource ne soit plus utilisée. Une application ne doit pas supprimer un stylet lorsque le stylet est sélectionné dans un contexte de périphérique.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#100](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]

##  <a name="createpenindirect"></a>  CPen::CreatePenIndirect

Initialise un stylet qui a le style, la largeur et la couleur donnés dans la structure vers laquelle pointe *lpLogPen*.

```
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```

### <a name="parameters"></a>Paramètres

*lpLogPen*<br/>
Pointe vers la structure Windows [logpen,](/windows/win32/api/Wingdi/ns-wingdi-logpen) qui contient des informations sur le stylet.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Les stylets dont la largeur est supérieure à 1 pixel doivent toujours avoir le style PS_NULL, PS_SOLID ou PS_INSIDEFRAME.

Si un stylet a le style PS_INSIDEFRAME et une couleur qui ne correspond pas à une couleur de la table des couleurs logiques, le stylet est dessiné avec une couleur déplacée. Le style PS_INSIDEFRAME est identique à PS_SOLID si la largeur du stylet est inférieure ou égale à 1.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#101](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]

##  <a name="fromhandle"></a>  CPen::FromHandle

Retourne un pointeur vers un `CPen` objet en fonction d’un handle vers un objet Pen Windows GDI.

```
static CPen* PASCAL FromHandle(HPEN hPen);
```

### <a name="parameters"></a>Paramètres

*hPen*<br/>
`HPEN`handle vers le stylet GDI Windows.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un `CPen` objet en cas de réussite; sinon, null.

### <a name="remarks"></a>Notes

Si aucun objet `CPen` n'est attaché au handle, un objet `CPen` temporaire est créé et attaché. Cet objet `CPen` temporaire est valide uniquement jusqu’à la prochaine période d’inactivité de l’application dans sa boucle d’événements, auquel cas tous les objets graphiques temporaires sont supprimés. En d’autres termes, l’objet temporaire n’est valide que pendant le traitement d’un message de fenêtre.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFCDocView#105](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]

##  <a name="getextlogpen"></a>  CPen::GetExtLogPen

Obtient une `EXTLOGPEN` structure sous-jacente.

```
int GetExtLogPen(EXTLOGPEN* pLogPen);
```

### <a name="parameters"></a>Paramètres

*pLogPen*<br/>
Pointe vers une structure [EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen) qui contient des informations sur le stylet.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La `EXTLOGPEN` structure définit les attributs de style, de largeur et de pinceau d’un stylet. Par exemple, appelez `GetExtLogPen` pour faire correspondre le style particulier d’un stylet.

Consultez les rubriques suivantes dans le SDK Windows pour plus d’informations sur les attributs de stylet:

- [GetObject](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen)

- [LOGPEN,](/windows/win32/api/wingdi/ns-wingdi-logpen)

- [ExtCreatePen](/windows/win32/api/wingdi/nf-wingdi-extcreatepen)

### <a name="example"></a>Exemple

L’exemple de code suivant montre `GetExtLogPen` comment appeler pour récupérer les attributs d’un stylet, puis créer un nouveau stylet cosmétique avec la même couleur.

[!code-cpp[NVC_MFCDocView#102](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]

##  <a name="getlogpen"></a>  CPen::GetLogPen

Obtient une `LOGPEN` structure sous-jacente.

```
int GetLogPen(LOGPEN* pLogPen);
```

### <a name="parameters"></a>Paramètres

*pLogPen*<br/>
Pointe vers une structure [logpen,](/windows/win32/api/wingdi/ns-wingdi-logpen) pour contenir des informations sur le stylet.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La `LOGPEN` structure définit le style, la couleur et le motif d’un stylet.

Par exemple, appelez `GetLogPen` pour faire correspondre le style particulier du stylet.

Consultez les rubriques suivantes dans le SDK Windows pour plus d’informations sur les attributs de stylet:

- [GetObject](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [LOGPEN,](/windows/win32/api/wingdi/ns-wingdi-logpen)

### <a name="example"></a>Exemple

L’exemple de code suivant montre `GetLogPen` comment appeler pour récupérer un caractère de stylet, puis créer un nouveau stylet plein avec la même couleur.

[!code-cpp[NVC_MFCDocView#103](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]

##  <a name="operator_hpen"></a>CPen:: Operator HPEN

Obtient le handle GDI Windows attaché de l' `CPen` objet.

```
operator HPEN() const;
```

### <a name="return-value"></a>Valeur de retour

En cas de réussite, handle vers l’objet Windows GDI représenté par `CPen` l’objet; sinon, null.

### <a name="remarks"></a>Notes

Cet opérateur est un opérateur de cast qui prend en charge l’utilisation directe d’un objet HPEN.

Pour plus d’informations sur l’utilisation des objets graphiques, consultez l’article [objets graphiques](/windows/win32/gdi/graphic-objects) dans SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#104](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]

## <a name="see-also"></a>Voir aussi

[CGdiObject, classe](../../mfc/reference/cgdiobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CBrush, classe](../../mfc/reference/cbrush-class.md)
