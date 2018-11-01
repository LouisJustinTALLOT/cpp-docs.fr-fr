---
title: CPen (classe)
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
ms.openlocfilehash: dc9216d10b620a79aa8e20e240791207f25a65c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531558"
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
|[CPen::CreatePen](#createpen)|Crée un stylet logique cosmétique ou géométrique avec le style spécifié, la largeur et les attributs de pinceau et l’attache à la `CPen` objet.|
|[CPen::CreatePenIndirect](#createpenindirect)|Crée un stylet avec le style, la largeur et la couleur donnée un [LOGPEN](/windows/desktop/api/wingdi/ns-wingdi-taglogpen) structure et l’attache à la `CPen` objet.|
|[CPen::FromHandle](#fromhandle)|Retourne un pointeur vers un `CPen` en fonction d’un HPEN Windows de l’objet.|
|[CPen::GetExtLogPen](#getextlogpen)|Obtient un [EXTLOGPEN](/windows/desktop/api/wingdi/ns-wingdi-tagextlogpen) structure sous-jacente.|
|[CPen::GetLogPen](#getlogpen)|Obtient un [LOGPEN](/windows/desktop/api/wingdi/ns-wingdi-taglogpen) structure sous-jacente.|

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

## <a name="requirements"></a>Configuration requise

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

*nPenStyle*<br/>
Spécifie le style du stylet. Ce paramètre dans la première version du constructeur peut être une des valeurs suivantes :

- PS_SOLID crée un stylet solid.

- PS_DASH crée un stylet en pointillés. Valide uniquement lorsque la largeur du stylet est 1 ou inférieure, appareil unités.

- PS_DOT crée un stylet en pointillés. Valide uniquement lorsque la largeur du stylet est 1 ou inférieure, appareil unités.

- PS_DASHDOT crée un stylet avec des ALTERNANCES de tirets et points. Valide uniquement lorsque la largeur du stylet est 1 ou inférieure, appareil unités.

- PS_DASHDOTDOT crée un stylet avec double points et des tirets alternés. Valide uniquement lorsque la largeur du stylet est 1 ou inférieure, appareil unités.

- PS_NULL crée un stylet null.

- Les fonctions qui spécifient un rectangle englobant de la sortie des PS_INSIDEFRAME crée un stylet qui dessine une ligne dans le cadre des formes fermées produit par l’interface GDI Windows (par exemple, le `Ellipse`, `Rectangle`, `RoundRect`, `Pie`et `Chord`fonctions membres). Quand ce style est utilisé avec les fonctions de sortie de Windows GDI qui ne spécifient pas d’un rectangle englobant (par exemple, le `LineTo` fonction membre), la zone de dessin du stylet n’est pas limitée par un frame.

La deuxième version de la `CPen` constructeur spécifie une combinaison de type, le style, extrémité de fin et les attributs de jointure. Les valeurs de chaque catégorie doivent être combinées à l’aide de l’opérateur OR au niveau du bit (&#124;). Le type de stylet peut prendre la valeur de l’une des valeurs suivantes :

- PS_GEOMETRIC crée un stylet géométrique.

- PS_COSMETIC crée un stylet.

   La deuxième version de la `CPen` constructeur ajoute les styles suivants de stylet pour *nPenStyle*:

- PS_ALTERNATE crée un stylet qui définit tous les autres pixels. (Ce style est applicable uniquement pour les stylets cosmétiques.)

- PS_USERSTYLE crée un stylet qui utilise un tableau de style fourni par l’utilisateur.

   L’extrémité de fin peut être une des valeurs suivantes :

- Embouts PS_ENDCAP_ROUND sont arrondis.

- Embouts PS_ENDCAP_SQUARE sont carrés.

- Embouts PS_ENDCAP_FLAT sont fixes.

   La jointure peut être une des valeurs suivantes :

- PS_JOIN_BEVEL joint sont en relief.

- PS_JOIN_MITER joint sont entre elles forment lorsqu’ils se trouvent dans la limite actuelle définie par le [SetMiterLimit](/windows/desktop/api/wingdi/nf-wingdi-setmiterlimit) (fonction). Si la jointure dépasse cette limite, il est en relief.

- PS_JOIN_ROUND joint sont arrondis.

*nWidth*<br/>
Spécifie la largeur du stylet.

- Pour la première version du constructeur, si cette valeur est 0, la largeur en unités de périphérique est toujours 1 pixel, quel que soit le mode de mappage.

- Pour la deuxième version du constructeur, si *nPenStyle* est PS_GEOMETRIC, la largeur est exprimée en unités logiques. Si *nPenStyle* est PS_COSMETIC, la largeur doit être définie sur 1.

*crColor*<br/>
Contient une couleur RVB pour le stylet.

*pLogBrush*<br/>
Pointe vers un `LOGBRUSH` structure. Si *nPenStyle* est PS_COSMETIC, le *lbColor* membre de la `LOGBRUSH` structure spécifie la couleur du stylet et le *lbStyle* membre de la `LOGBRUSH` structure doit être définie sur BS_SOLID. Si *nPenStyle* est PS_GEOMETRIC, tous les membres doivent être utilisés pour spécifier les attributs de pinceau du stylet.

*nStyleCount*<br/>
Spécifie la longueur, en unités de mot double, de la *lpStyle* tableau. Cette valeur doit être zéro si *nPenStyle* n’est pas PS_USERSTYLE.

*lpStyle*<br/>
Pointe vers un tableau de valeurs de mot double. La première valeur spécifie la longueur du premier tiret dans un style défini par l’utilisateur, la deuxième valeur spécifie la longueur de l’espace premier et ainsi de suite. Ce pointeur doit être NULL si *nPenStyle* n’est pas PS_USERSTYLE.

### <a name="remarks"></a>Notes

Si vous utilisez le constructeur sans arguments, vous devez initialiser résultant `CPen` de l’objet avec le `CreatePen`, `CreatePenIndirect`, ou `CreateStockObject` fonctions membres.

Si vous utilisez le constructeur qui prend des arguments, aucune initialisation supplémentaire n’est nécessaire. Le constructeur avec des arguments peut lever une exception si des erreurs sont rencontrées, tandis que le constructeur sans arguments réussira toujours.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#99](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]

##  <a name="createpen"></a>  CPen::CreatePen

Crée un stylet logique cosmétique ou géométrique avec le style spécifié, la largeur et les attributs de pinceau et l’attache à la `CPen` objet.

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
Spécifie le style pour le stylet. Pour obtenir la liste des valeurs possibles, consultez le *nPenStyle* paramètre dans le [CPen](#cpen) constructeur.

*nWidth*<br/>
Spécifie la largeur du stylet.

- Pour la première version de `CreatePen`, si cette valeur est 0, la largeur en unités de périphérique est toujours 1 pixel, quel que soit le mode de mappage.

- Pour la deuxième version de `CreatePen`si *nPenStyle* est PS_GEOMETRIC, la largeur est exprimée en unités logiques. Si *nPenStyle* est PS_COSMETIC, la largeur doit être définie sur 1.

*crColor*<br/>
Contient une couleur RVB pour le stylet.

*pLogBrush*<br/>
Pointe vers un [LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush) structure. Si *nPenStyle* est PS_COSMETIC, le `lbColor` membre de la `LOGBRUSH` structure spécifie la couleur du stylet et le *lbStyle* membre de la `LOGBRUSH` structure doit être définie sur BS_ SOLIDE. Si nPenStyle est PS_GEOMETRIC, tous les membres doivent être utilisés pour spécifier les attributs de pinceau du stylet.

*nStyleCount*<br/>
Spécifie la longueur, en unités de mot double, de la *lpStyle* tableau. Cette valeur doit être zéro si *nPenStyle* n’est pas PS_USERSTYLE.

*lpStyle*<br/>
Pointe vers un tableau de valeurs de mot double. La première valeur spécifie la longueur du premier tiret dans un style défini par l’utilisateur, la deuxième valeur spécifie la longueur de l’espace premier et ainsi de suite. Ce pointeur doit être NULL si *nPenStyle* n’est pas PS_USERSTYLE.

### <a name="return-value"></a>Valeur de retour

Différent de zéro en cas de réussite, ou zéro si la méthode échoue.

### <a name="remarks"></a>Notes

La première version de `CreatePen` Initialise un stylet avec le style spécifié, la largeur et la couleur. Le stylet peut être sélectionné par la suite en tant que le stylet actuel pour n’importe quel contexte de périphérique.

Stylets qui ont une largeur supérieure à 1 pixel doivent toujours avoir le PS_NULL, PS_SOLID, PS_INSIDEFRAME style ou.

Si un stylet a le style PS_INSIDEFRAME et une couleur qui ne correspond pas à une couleur de la table logique, le stylet est dessiné avec une couleur dégradée. Le style de stylet PS_SOLID ne peut pas être utilisé pour créer un stylet avec une couleur dégradée. Le style PS_INSIDEFRAME est identique à PS_SOLID si la largeur du stylet est inférieure ou égale à 1.

La deuxième version de `CreatePen` Initialise un stylet logique cosmétique ou géométrique qui a la valeur du style, la largeur et attributs de pinceau. La largeur d’un stylet est toujours 1 ; la largeur d’un stylet géométrique est toujours spécifiée en unités universelles. Une fois une application crée un stylet logique, il peut sélectionner ce dans un contexte de périphérique en appelant le [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) (fonction). Après la sélection d’un stylet dans un contexte de périphérique, il peut être utilisé pour dessiner des lignes et des courbes.

- Si *nPenStyle* est PS_COSMETIC et PS_USERSTYLE, les entrées dans le *lpStyle* tableau spécifie les longueurs des tirets et des espaces dans les unités de style. Une unité de style est définie par l’appareil dans lequel le stylet est utilisé pour dessiner une ligne.

- Si *nPenStyle* est PS_GEOMETRIC et PS_USERSTYLE, les entrées dans le *lpStyle* tableau spécifie les longueurs des tirets et des espaces en unités logiques.

- Si *nPenStyle* est PS_ALTERNATE, l’unité de style est ignorée et tous les autres pixels est défini.

Lorsqu’une application ne requiert plus un stylet donné, il doit appeler la [CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) membre de fonction ou de détruire le `CPen` afin de la ressource n’est plus en cours d’utilisation de l’objet. Une application ne doit pas supprimer un stylet lorsque le stylet est sélectionné dans un contexte de périphérique.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#100](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]

##  <a name="createpenindirect"></a>  CPen::CreatePenIndirect

Initialise un stylet qui a le style, la largeur et la couleur indiquée dans la structure vers laquelle pointe *lpLogPen*.

```
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```

### <a name="parameters"></a>Paramètres

*lpLogPen*<br/>
Pointe vers le Windows [LOGPEN](../../mfc/reference/logpen-structure.md) structure qui contient des informations sur le stylet.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Stylets qui ont une largeur supérieure à 1 pixel doivent toujours avoir le PS_NULL, PS_SOLID, PS_INSIDEFRAME style ou.

Si un stylet a le style PS_INSIDEFRAME et une couleur qui ne correspond pas à une couleur de la table logique, le stylet est dessiné avec une couleur dégradée. Le style PS_INSIDEFRAME est identique à PS_SOLID si la largeur du stylet est inférieure ou égale à 1.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#101](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]

##  <a name="fromhandle"></a>  CPen::FromHandle

Retourne un pointeur vers un `CPen` objet en fonction d’un handle à un objet de stylet Windows GDI.

```
static CPen* PASCAL FromHandle(HPEN hPen);
```

### <a name="parameters"></a>Paramètres

*hPen*<br/>
`HPEN` handle de stylet de Windows GDI.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un `CPen` objet en cas de réussite ; sinon, NULL.

### <a name="remarks"></a>Notes

Si aucun objet `CPen` n'est attaché au handle, un objet `CPen` temporaire est créé et attaché. Ce fichier temporaire `CPen` objet est valide uniquement jusqu'à ce que la prochaine fois que l’application possède les temps d’inactivité dans sa boucle de l’événement, alors graphique temporaire de tous les objets sont supprimés. En d’autres termes, l’objet temporaire est uniquement valide pendant le traitement du message d’une fenêtre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#105](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]

##  <a name="getextlogpen"></a>  CPen::GetExtLogPen

Obtient un `EXTLOGPEN` structure sous-jacente.

```
int GetExtLogPen(EXTLOGPEN* pLogPen);
```

### <a name="parameters"></a>Paramètres

*pLogPen*<br/>
Pointe vers une [EXTLOGPEN](/windows/desktop/api/wingdi/ns-wingdi-tagextlogpen) structure qui contient des informations sur le stylet.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le `EXTLOGPEN` structure définit le style, la largeur et les attributs de pinceau d’un stylet. Par exemple, appeler `GetExtLogPen` pour faire correspondre le style particulier d’un stylet.

Consultez les rubriques suivantes dans le SDK Windows pour plus d’informations sur les attributs de stylet :

- [GetObject](/windows/desktop/api/wingdi/nf-wingdi-getobject)

- [EXTLOGPEN](/windows/desktop/api/wingdi/ns-wingdi-tagextlogpen)

- [LOGPEN](/windows/desktop/api/wingdi/ns-wingdi-taglogpen)

- [ExtCreatePen](/windows/desktop/api/wingdi/nf-wingdi-extcreatepen)

### <a name="example"></a>Exemple

L’exemple de code suivant montre l’appel `GetExtLogPen` pour récupérer les attributs d’un stylet et ensuite créer un stylet de nouveau, cosmétique avec la même couleur.

[!code-cpp[NVC_MFCDocView#102](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]

##  <a name="getlogpen"></a>  CPen::GetLogPen

Obtient un `LOGPEN` structure sous-jacente.

```
int GetLogPen(LOGPEN* pLogPen);
```

### <a name="parameters"></a>Paramètres

*pLogPen*<br/>
Pointe vers un [LOGPEN](/windows/desktop/api/wingdi/ns-wingdi-taglogpen) structure destinée à contenir des informations sur le stylet.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le `LOGPEN` structure définit le style, la couleur et le modèle d’un stylet.

Par exemple, appeler `GetLogPen` pour faire correspondre le type particulier de stylet.

Consultez les rubriques suivantes dans le SDK Windows pour plus d’informations sur les attributs de stylet :

- [GetObject](/windows/desktop/api/wingdi/nf-wingdi-getobject)

- [LOGPEN](/windows/desktop/api/wingdi/ns-wingdi-taglogpen)

### <a name="example"></a>Exemple

L’exemple de code suivant montre l’appel `GetLogPen` pour récupérer un caractère de stylet et puis créer un nouveau stylet solid avec la même couleur.

[!code-cpp[NVC_MFCDocView#103](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]

##  <a name="operator_hpen"></a>  CPen::operator HPEN

Obtient le handle Windows GDI attaché de la `CPen` objet.

```
operator HPEN() const;
```

### <a name="return-value"></a>Valeur de retour

Si réussie, un handle vers l’objet de Windows GDI représenté par le `CPen` de l’objet ; sinon, NULL.

### <a name="remarks"></a>Notes

Cet opérateur est un opérateur de cast, qui prend en charge l’utilisation directe d’un objet HPEN.

Pour plus d’informations sur l’utilisation des objets graphiques, consultez l’article [graphique objets](/windows/desktop/gdi/graphic-objects) dans le Kit de développement logiciel Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#104](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]

## <a name="see-also"></a>Voir aussi

[CGdiObject, classe](../../mfc/reference/cgdiobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CBrush, classe](../../mfc/reference/cbrush-class.md)
