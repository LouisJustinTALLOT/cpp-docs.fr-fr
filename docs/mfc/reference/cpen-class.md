---
title: Classe CPen
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
ms.openlocfilehash: e15dc53fafa0d80f1b52b3fe77f3635c592a4346
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364082"
---
# <a name="cpen-class"></a>Classe CPen

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
|[CPen::CreatePen](#createpen)|Crée un stylo cosmétique ou géométrique logique avec le style spécifié, `CPen` la largeur et les attributs de brosse, et le fixe à l’objet.|
|[CPen::CreatePenIndirect](#createpenindirect)|Crée un stylo avec le style, la largeur et la couleur donné `CPen` dans une structure [LOGPEN,](/windows/win32/api/wingdi/ns-wingdi-logpen) et le fixe à l’objet.|
|[CPen::DeHandle](#fromhandle)|Retourne un pointeur à un `CPen` objet lorsqu’on lui donne un HPEN Windows.|
|[CPen::GetExtLogPen](#getextlogpen)|Obtient une structure sous-jacente [EXTLOGPEN.](/windows/win32/api/wingdi/ns-wingdi-extlogpen)|
|[CPen::GetLogPen](#getlogpen)|Obtient une structure sous-jacente [LOGPEN.](/windows/win32/api/wingdi/ns-wingdi-logpen)|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CPen::opérateur HPEN](#operator_hpen)|Retourne la poignée Windows `CPen` attachée à l’objet.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur l’utilisation `CPen`, voir Objets [graphiques](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPen`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cpencpen"></a><a name="cpen"></a>CPen::CPen

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

*nPenStyle (en anglais)*<br/>
Spécifie le style de stylo. Ce paramètre dans la première version du constructeur peut être l’une des valeurs suivantes :

- PS_SOLID crée un stylo solide.

- PS_DASH crée un stylo pointillé. Valable uniquement lorsque la largeur du stylo est de 1 ou moins, dans les unités de l’appareil.

- PS_DOT crée un stylo pointillé. Valable uniquement lorsque la largeur du stylo est de 1 ou moins, dans les unités de l’appareil.

- PS_DASHDOT crée un stylo avec des tirets et des points en alternance. Valable uniquement lorsque la largeur du stylo est de 1 ou moins, dans les unités de l’appareil.

- PS_DASHDOTDOT crée un stylo avec des tirets et des doubles points en alternance. Valable uniquement lorsque la largeur du stylo est de 1 ou moins, dans les unités de l’appareil.

- PS_NULL crée un stylo nul.

- PS_INSIDEFRAME Crée un stylo qui trace une ligne à l’intérieur du cadre de formes fermées produites `Ellipse`par `Rectangle` `RoundRect`les `Pie`fonctions de sortie De Windows GDI qui spécifient un rectangle de délimitation (par exemple, le , , , et `Chord` les fonctions des membres). Lorsque ce style est utilisé avec les fonctions de sortie De Windows `LineTo` GDI qui ne spécifient pas un rectangle de délimitation (par exemple, la fonction membre), la zone de dessin du stylo n’est pas limitée par un cadre.

La deuxième version `CPen` du constructeur spécifie une combinaison de types, de style, de bouchon d’extrémité et d’attributs de jointure. Les valeurs de chaque catégorie doivent être combinées en utilisant l’opérateur BITwise OR (&#124;). Le type de stylo peut être l’une des valeurs suivantes :

- PS_GEOMETRIC crée un stylo géométrique.

- PS_COSMETIC crée un stylo cosmétique.

   La deuxième version `CPen` du constructeur ajoute les styles de stylo suivants pour *nPenStyle*:

- PS_ALTERNATE crée un stylo qui définit tous les autres pixels. (Ce style ne s’applique que pour les stylos cosmétiques.)

- PS_USERSTYLE crée un stylo qui utilise un tableau de style fourni par l’utilisateur.

   Le plafond final peut être l’une des valeurs suivantes :

- PS_ENDCAP_ROUND Les casquettes de fin sont rondes.

- PS_ENDCAP_SQUARE Les bouchons d’extrémité sont carrés.

- PS_ENDCAP_FLAT les bouchons d’extrémité sont plats.

   La jointure peut être l’une des valeurs suivantes :

- PS_JOIN_BEVEL jointures sont biseautées.

- PS_JOIN_MITER Joints sont mitered quand ils sont dans la limite actuelle définie par la fonction [SetMiterLimit.](/windows/win32/api/wingdi/nf-wingdi-setmiterlimit) Si la jointure dépasse cette limite, elle est biseautée.

- PS_JOIN_ROUND joints sont ronds.

*nWidth (en)*<br/>
Spécifie la largeur du stylo.

- Pour la première version du constructeur, si cette valeur est de 0, la largeur des unités de l’appareil est toujours de 1 pixel, quel que soit le mode de cartographie.

- Pour la deuxième version du constructeur, si *nPenStyle* est PS_GEOMETRIC, la largeur est donnée en unités logiques. Si *nPenStyle* est PS_COSMETIC, la largeur doit être réglée à 1.

*crColor (en)*<br/>
Contient une couleur RGB pour le stylo.

*pLogBrush (en)*<br/>
Points à `LOGBRUSH` une structure. Si *nPenStyle* est PS_COSMETIC, le membre *lbColor* de la `LOGBRUSH` structure spécifie la couleur du stylo et le membre *lbStyle* de la `LOGBRUSH` structure doit être mis à BS_SOLID. Si *nPenStyle* est PS_GEOMETRIC, tous les membres doivent être utilisés pour spécifier les attributs de pinceau du stylo.

*nStyleCount (en)*<br/>
Spécifie la longueur, en double mot, du tableau *lpStyle.* Cette valeur doit être nulle si *nPenStyle* n’est pas PS_USERSTYLE.

*lpStyle (en)*<br/>
Points à un tableau de valeurs de double mot. La première valeur spécifie la longueur du premier tableau de bord dans un style défini par l’utilisateur, la deuxième valeur spécifie la longueur du premier espace, et ainsi de suite. Ce pointeur doit être NULL si *nPenStyle* n’est pas PS_USERSTYLE.

### <a name="remarks"></a>Notes

Si vous utilisez le constructeur sans arguments, vous `CPen` devez `CreatePen`initialiser l’objet résultant avec les fonctions, `CreatePenIndirect`ou `CreateStockObject` les fonctions des membres.

Si vous utilisez le constructeur qui prend des arguments, alors aucune autre initialisation n’est nécessaire. Le constructeur avec des arguments peut jeter une exception si des erreurs sont rencontrées, tandis que le constructeur sans arguments réussira toujours.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#99](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]

## <a name="cpencreatepen"></a><a name="createpen"></a>CPen::CreatePen

Crée un stylo cosmétique ou géométrique logique avec le style spécifié, `CPen` la largeur et les attributs de brosse, et le fixe à l’objet.

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

*nPenStyle (en anglais)*<br/>
Spécifie le style de la plume. Pour une liste de valeurs possibles, voir le paramètre *nPenStyle* dans le constructeur [CPen.](#cpen)

*nWidth (en)*<br/>
Spécifie la largeur du stylo.

- Pour la première `CreatePen`version de , si cette valeur est de 0, la largeur dans les unités de périphérique est toujours 1 pixel, quel que soit le mode de cartographie.

- Pour la deuxième `CreatePen`version de , si *nPenStyle* est PS_GEOMETRIC, la largeur est donnée en unités logiques. Si *nPenStyle* est PS_COSMETIC, la largeur doit être réglée à 1.

*crColor (en)*<br/>
Contient une couleur RGB pour le stylo.

*pLogBrush (en)*<br/>
Indique une structure [LOGBRUSH.](/windows/win32/api/wingdi/ns-wingdi-logbrush) Si *nPenStyle* est PS_COSMETIC, `lbColor` le membre `LOGBRUSH` de la structure spécifie la couleur `LOGBRUSH` du stylo et le membre *lbStyle* de la structure doit être mis à BS_SOLID. Si nPenStyle est PS_GEOMETRIC, tous les membres doivent être utilisés pour spécifier les attributs de pinceau du stylo.

*nStyleCount (en)*<br/>
Spécifie la longueur, en double mot, du tableau *lpStyle.* Cette valeur doit être nulle si *nPenStyle* n’est pas PS_USERSTYLE.

*lpStyle (en)*<br/>
Points à un tableau de valeurs de double mot. La première valeur spécifie la longueur du premier tableau de bord dans un style défini par l’utilisateur, la deuxième valeur spécifie la longueur du premier espace, et ainsi de suite. Ce pointeur doit être NULL si *nPenStyle* n’est pas PS_USERSTYLE.

### <a name="return-value"></a>Valeur de retour

Nonzero en cas de succès, ou zéro si la méthode échoue.

### <a name="remarks"></a>Notes

La première `CreatePen` version de l’initialisation d’un stylo avec le style spécifié, la largeur et la couleur. Le stylo peut ensuite être sélectionné comme le stylo actuel pour n’importe quel contexte de périphérique.

Les stylos dont la largeur est supérieure à 1 pixel doivent toujours avoir le PS_NULL, PS_SOLID ou PS_INSIDEFRAME style.

Si un stylo a le style PS_INSIDEFRAME et une couleur qui ne correspond pas à une couleur dans la table de couleur logique, le stylo est dessiné avec une couleur tergiversée. Le style PS_SOLID stylo ne peut pas être utilisé pour créer un stylo avec une couleur tergiversée. Le style PS_INSIDEFRAME est identique à PS_SOLID si la largeur du stylo est inférieure ou égale à 1.

La deuxième `CreatePen` version de l’initialisation d’un stylo cosmétique ou géométrique logique qui a le style spécifié, la largeur et les attributs de pinceau. La largeur d’un stylo cosmétique est toujours 1; la largeur d’un stylo géométrique est toujours spécifiée en unités du monde. Après qu’une application crée un stylo logique, il peut sélectionner ce stylo dans un contexte d’appareil en appelant la fonction [CDC::SelectObject.](../../mfc/reference/cdc-class.md#selectobject) Une fois qu’un stylo est sélectionné dans un contexte d’appareil, il peut être utilisé pour tracer des lignes et des courbes.

- Si *nPenStyle* est PS_COSMETIC et PS_USERSTYLE, les entrées dans le tableau *lpStyle* spécifient des longueurs de tirets et d’espaces dans les unités de style. Une unité de style est définie par l’appareil dans lequel le stylo est utilisé pour tracer une ligne.

- Si *nPenStyle* est PS_GEOMETRIC et PS_USERSTYLE, les entrées dans le tableau *lpStyle* spécifient des longueurs de tirets et d’espaces dans des unités logiques.

- Si *nPenStyle* est PS_ALTERNATE, l’unité de style est ignorée et tous les autres pixels sont définis.

Lorsqu’une application n’a plus besoin d’un stylo donné, elle doit appeler le [CGdiObject: :DleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) fonction membre ou détruire l’objet `CPen` de sorte que la ressource n’est plus en usage. Une application ne doit pas supprimer un stylo lorsque le stylet est sélectionné dans un contexte d’appareil.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#100](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]

## <a name="cpencreatepenindirect"></a><a name="createpenindirect"></a>CPen::CreatePenIndirect

Initialise un stylo qui a le style, la largeur et la couleur donnée dans la structure indiquée par *lpLogPen*.

```
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```

### <a name="parameters"></a>Paramètres

*lpLogPen (en anglais)*<br/>
Points à la structure Windows [LOGPEN](/windows/win32/api/Wingdi/ns-wingdi-logpen) qui contient des informations sur le stylo.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Les stylos dont la largeur est supérieure à 1 pixel doivent toujours avoir le PS_NULL, PS_SOLID ou PS_INSIDEFRAME style.

Si un stylo a le style PS_INSIDEFRAME et une couleur qui ne correspond pas à une couleur dans la table de couleur logique, le stylo est dessiné avec une couleur tergiversée. Le style PS_INSIDEFRAME est identique à PS_SOLID si la largeur du stylo est inférieure ou égale à 1.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#101](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]

## <a name="cpenfromhandle"></a><a name="fromhandle"></a>CPen::DeHandle

Retourne un pointeur à un `CPen` objet donné une poignée à un objet de style Windows GDI.

```
static CPen* PASCAL FromHandle(HPEN hPen);
```

### <a name="parameters"></a>Paramètres

*hPen (en anglais)*<br/>
`HPEN`poignée de style windows GDI.

### <a name="return-value"></a>Valeur de retour

Un pointeur `CPen` à un objet en cas de succès; autrement NULL.

### <a name="remarks"></a>Notes

Si aucun objet `CPen` n'est attaché au handle, un objet `CPen` temporaire est créé et attaché. Cet `CPen` objet temporaire n’est valable que jusqu’à la prochaine fois que l’application a un temps d’inactivité dans sa boucle d’événement, date à laquelle tous les objets graphiques temporaires sont supprimés. En d’autres termes, l’objet temporaire n’est valable que pendant le traitement d’un message de fenêtre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#105](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]

## <a name="cpengetextlogpen"></a><a name="getextlogpen"></a>CPen::GetExtLogPen

Obtient `EXTLOGPEN` une structure sous-jacente.

```
int GetExtLogPen(EXTLOGPEN* pLogPen);
```

### <a name="parameters"></a>Paramètres

*pLogPen (en anglais)*<br/>
Indique une structure [EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen) qui contient des informations sur le stylo.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La `EXTLOGPEN` structure définit le style, la largeur et les attributs de pinceau d’un stylo. Par exemple, `GetExtLogPen` appelez pour correspondre au style particulier d’un stylo.

Voir les sujets suivants dans le Windows SDK pour plus d’informations sur les attributs du stylo :

- [Getobject](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen)

- [LOGPEN (EN ANGLAIS)](/windows/win32/api/wingdi/ns-wingdi-logpen)

- [ExtCreatePen](/windows/win32/api/wingdi/nf-wingdi-extcreatepen)

### <a name="example"></a>Exemple

L’exemple de code `GetExtLogPen` suivant montre l’appel pour récupérer les attributs d’un stylo, puis créer un nouveau stylo cosmétique avec la même couleur.

[!code-cpp[NVC_MFCDocView#102](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]

## <a name="cpengetlogpen"></a><a name="getlogpen"></a>CPen::GetLogPen

Obtient `LOGPEN` une structure sous-jacente.

```
int GetLogPen(LOGPEN* pLogPen);
```

### <a name="parameters"></a>Paramètres

*pLogPen (en anglais)*<br/>
Indique une structure [LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen) pour contenir des informations sur le stylo.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La `LOGPEN` structure définit le style, la couleur et le motif d’un stylo.

Par exemple, `GetLogPen` appelez pour correspondre au style particulier de la plume.

Voir les sujets suivants dans le Windows SDK pour plus d’informations sur les attributs du stylo :

- [Getobject](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [LOGPEN (EN ANGLAIS)](/windows/win32/api/wingdi/ns-wingdi-logpen)

### <a name="example"></a>Exemple

L’exemple de code `GetLogPen` suivant montre l’appel pour récupérer un personnage de stylet, puis créer un nouveau stylo solide avec la même couleur.

[!code-cpp[NVC_MFCDocView#103](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]

## <a name="cpenoperator-hpen"></a><a name="operator_hpen"></a>CPen::opérateur HPEN

Obtient la poignée Windows GDI attachée de l’objet. `CPen`

```
operator HPEN() const;
```

### <a name="return-value"></a>Valeur de retour

En cas de succès, une poignée à `CPen` l’objet GDI Windows représenté par l’objet; autrement NULL.

### <a name="remarks"></a>Notes

Cet opérateur est un opérateur de coulée, qui prend en charge l’utilisation directe d’un objet HPEN.

Pour plus d’informations sur l’utilisation d’objets graphiques, voir l’article [Graphic Objects](/windows/win32/gdi/graphic-objects) in Windows SDK.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#104](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]

## <a name="see-also"></a>Voir aussi

[CGdiObject, classe](../../mfc/reference/cgdiobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CBrush, classe](../../mfc/reference/cbrush-class.md)
