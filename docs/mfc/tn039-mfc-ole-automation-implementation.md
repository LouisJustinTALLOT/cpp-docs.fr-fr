---
description: 'En savoir plus sur : TN039 : implémentation d’Automation MFC/OLE'
title: 'TN039 : implémentation d’Automation MFC-OLE'
ms.date: 06/28/2018
helpviewer_keywords:
- MFC, COM support
- IDispatch interface
- MFC, OLE DB and
- TN039
- Automation, MFC COM interface entry points
ms.assetid: 765fa3e9-dd54-4f08-9ad2-26e0546ff8b6
ms.openlocfilehash: caabd3719a467e534e47ca61ed8f9a9f1f0d2eb6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215415"
---
# <a name="tn039-mfcole-automation-implementation"></a>TN039 : implémentation d'Automation MFC/OLE

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

## <a name="overview-of-ole-idispatch-interface"></a>Vue d’ensemble de l’interface OLE IDispatch

L' `IDispatch` interface est le moyen par lequel les applications exposent des méthodes et des propriétés afin que d’autres applications, telles que Visual Basic, ou d’autres langages, puissent utiliser les fonctionnalités de l’application. La partie la plus importante de cette interface est la `IDispatch::Invoke` fonction. MFC utilise des « tables de dispatch » pour implémenter `IDispatch::Invoke` . La table de dispatch fournit les informations d’implémentation MFC sur la disposition ou la « forme » de vos `CCmdTarget` classes dérivées de, de telle sorte qu’elle peut manipuler directement les propriétés de l’objet ou appeler des fonctions membres dans votre objet pour répondre aux `IDispatch::Invoke` demandes.

Dans la plupart des cas, ClassWizard et MFC coopèrent pour masquer la plupart des détails d’OLE Automation à partir du programmeur de l’application. Le programmeur se focalise sur les fonctionnalités réelles à exposer dans l’application et n’a pas à se soucier de la plomberie sous-jacente.

Toutefois, il existe des cas où il est nécessaire de comprendre ce que fait MFC en arrière-plan. Cette note traitera la façon dont l’infrastructure assigne les **DISPID** s aux fonctions et propriétés membres. La connaissance de l’algorithme utilisé par MFC pour assigner des **DISPID** s n’est nécessaire que si vous avez besoin de connaître les ID, par exemple lorsque vous créez une « bibliothèque de types » pour les objets de votre application.

## <a name="mfc-dispid-assignment"></a>Assignation MFC DISPID

Bien que l’utilisateur final d’Automation (un utilisateur Visual Basic, par exemple), voit les noms réels des propriétés et méthodes activées par Automation dans leur code (tel que obj. ShowWindow), l’implémentation de `IDispatch::Invoke` ne reçoit pas les noms réels. Pour des raisons d’optimisation, il reçoit un **DISPID**, qui est un « Magic cookie » 32 bits qui décrit la méthode ou la propriété à laquelle accéder. Ces valeurs **DISPID** sont retournées à partir de l' `IDispatch` implémentation par le biais d’une autre méthode, appelée `IDispatch::GetIDsOfNames` . Une application cliente Automation appellera `GetIDsOfNames` une fois pour chaque membre ou propriété à laquelle elle envisage d’accéder, et les met en cache pour les appels ultérieurs à `IDispatch::Invoke` . De cette façon, la recherche de chaînes coûteuse n’est effectuée qu’une seule fois par objet, et non une fois par `IDispatch::Invoke` appel.

MFC détermine les **DISPID** pour chaque méthode et propriété en fonction des deux éléments suivants :

- Distance à partir du haut de la table de dispatch (1 relatif)

- Distance de la table de dispatch de la classe la plus dérivée (0 relatif)

Le **DISPID** est divisé en deux parties. Le **LOWORD** du **DISPID** contient le premier composant, la distance à partir du haut de la table de dispatch. Le **HIWORD** contient la distance de la classe la plus dérivée. Par exemple :

```cpp
class CDispPoint : public CCmdTarget
{
public:
    short m_x, m_y;
    // ...
    DECLARE_DISPATCH_MAP()
    // ...
};

class CDisp3DPoint : public CDispPoint
{
public:
    short m_z;
    // ...
    DECLARE_DISPATCH_MAP()
    // ...
};

BEGIN_DISPATCH_MAP(CDispPoint, CCmdTarget)
    DISP_PROPERTY(CDispPoint, "x", m_x, VT_I2)
    DISP_PROPERTY(CDispPoint, "y", m_y, VT_I2)
END_DISPATCH_MAP()

BEGIN_DISPATCH_MAP(CDisp3DPoint, CDispPoint)
    DISP_PROPERTY(CDisp3DPoint, "z", m_z, VT_I2)
END_DISPATCH_MAP()
```

Comme vous pouvez le voir, il existe deux classes, qui exposent toutes les deux les interfaces OLE Automation. L’une de ces classes est dérivée de l’autre et tire donc parti des fonctionnalités de la classe de base, y compris de la partie OLE Automation (les propriétés « x » et « y » dans ce cas).

MFC génère des **DISPID** s pour la classe CDispPoint comme suit :

```cpp
property X    (DISPID)0x00000001
property Y    (DISPID)0x00000002
```

Étant donné que les propriétés ne sont pas dans une classe de base, le **HIWORD** du **DISPID** est toujours égal à zéro (la distance entre la classe la plus dérivée pour CDispPoint est égale à zéro).

MFC génère des **DISPID** s pour la classe CDisp3DPoint comme suit :

```cpp
property Z    (DISPID)0x00000001
property X    (DISPID)0x00010001
property Y    (DISPID)0x00010002
```

La propriété Z reçoit un **DISPID** avec un zéro **HIWORD** , car il est défini dans la classe qui expose les propriétés, CDisp3DPoint. Étant donné que les propriétés X et Y sont définies dans une classe de base, le **HIWORD** du **DISPID** est 1, puisque la classe dans laquelle ces propriétés sont définies se trouve à une distance d’une dérivation de la classe la plus dérivée.

> [!NOTE]
> Le **LOWORD** est toujours déterminé par la position dans le mappage, même s’il existe des entrées dans le mappage avec **DISPID** explicite (consultez la section suivante pour plus d’informations sur les versions **_id** des `DISP_PROPERTY` `DISP_FUNCTION` macros et).

## <a name="advanced-mfc-dispatch-map-features"></a>Fonctionnalités avancées de la table de dispatch MFC

ClassWizard ne prend pas en charge plusieurs fonctionnalités supplémentaires avec cette version de Visual C++. ClassWizard prend en charge `DISP_FUNCTION` , `DISP_PROPERTY` et `DISP_PROPERTY_EX` qui définissent respectivement une méthode, une propriété de variable membre et une propriété de fonction membre obtenir/définir. Ces fonctionnalités sont généralement toutes nécessaires pour créer la plupart des serveurs Automation.

Les macros supplémentaires suivantes peuvent être utilisées lorsque les macros prises en charge par l’Assistant ne sont pas appropriées : `DISP_PROPERTY_NOTIFY` et `DISP_PROPERTY_PARAM` .

## <a name="disp_property_notify--macro-description"></a>DISP_PROPERTY_NOTIFY : description de la macro

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    pszName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
Nom de la classe.

*pszName*<br/>
Nom externe de la propriété.

*memberName*<br/>
Nom de la variable membre dans laquelle la propriété est stockée.

*pfnAfterSet*<br/>
Nom de la fonction membre à appeler lorsque la propriété est modifiée.

*vtPropType*<br/>
Valeur qui spécifie le type de la propriété.

### <a name="remarks"></a>Notes

Cette macro est semblable à DISP_PROPERTY, à ceci près qu’elle accepte un argument supplémentaire. L’argument supplémentaire, *pfnAfterSet,* doit être une fonction membre qui ne retourne rien et ne prend pas de paramètres, 'void OnPropertyNotify () '. Elle est appelée **une fois que** la variable membre a été modifiée.

## <a name="disp_property_param--macro-description"></a>DISP_PROPERTY_PARAM : description de la macro

```cpp
DISP_PROPERTY_PARAM(
    theClass,
    pszName,
    pfnGet,
    pfnSet,
    vtPropType,
    vtsParams)
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
Nom de la classe.

*pszName*<br/>
Nom externe de la propriété.

*memberGet*<br/>
Nom de la fonction membre utilisée pour accéder à la propriété.

*PEL*<br/>
Nom de la fonction membre utilisée pour définir la propriété.

*vtPropType*<br/>
Valeur qui spécifie le type de la propriété.

*vtsParams*<br/>
Chaîne d’espaces séparés VTS_ pour chaque paramètre.

### <a name="remarks"></a>Notes

À l’instar de la macro DISP_PROPERTY_EX, cette macro définit une propriété accessible avec des fonctions membres d’extraction et de définition distinctes. Cette macro, toutefois, vous permet de spécifier une liste de paramètres pour la propriété. Cela est utile pour implémenter des propriétés indexées ou paramétrées d’une autre façon. Les paramètres sont toujours placés en premier, suivis de la nouvelle valeur de la propriété. Par exemple :

```cpp
DISP_PROPERTY_PARAM(CMyObject, "item", GetItem, SetItem, VT_DISPATCH, VTS_I2 VTS_I2)
```

correspondrait aux fonctions membres d’extraction et de définition :

```cpp
LPDISPATCH CMyObject::GetItem(short row, short col)
void CMyObject::SetItem(short row, short col, LPDISPATCH newValue)
```

## <a name="disp_xxxx_id--macro-descriptions"></a>DISP_XXXX_ID : descriptions des macros

```cpp
DISP_FUNCTION_ID(
    theClass,
    pszName,
    dispid,
    pfnMember,
    vtRetVal,
    vtsParams)
DISP_PROPERTY_ID(
    theClass,
    pszName,
    dispid,
    memberName,
    vtPropType)
DISP_PROPERTY_NOTIFY_ID(
    theClass,
    pszName,
    dispid,
    memberName,
    pfnAfterSet,
    vtPropType)
DISP_PROPERTY_EX_ID(
    theClass,
    pszName,
    dispid,
    pfnGet,
    pfnSet,
    vtPropType)
DISP_PROPERTY_PARAM_ID(
    theClass,
    pszName,
    dispid,
    pfnGet,
    pfnSet,
    vtPropType,
    vtsParams)
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
Nom de la classe.

*pszName*<br/>
Nom externe de la propriété.

*égal*<br/>
DISPID fixe pour la propriété ou la méthode.

*pfnGet*<br/>
Nom de la fonction membre utilisée pour accéder à la propriété.

*pfnSet*<br/>
Nom de la fonction membre utilisée pour définir la propriété.

*memberName*<br/>
Nom de la variable membre à mapper à la propriété.

*vtPropType*<br/>
Valeur qui spécifie le type de la propriété.

*vtsParams*<br/>
Chaîne d’espaces séparés VTS_ pour chaque paramètre.

### <a name="remarks"></a>Notes

Ces macros vous permettent de spécifier un **DISPID** au lieu de laisser MFC en assigner automatiquement un. Ces macros avancées ont les mêmes noms, sauf que l’ID est ajouté au nom de la macro (par exemple, **DISP_PROPERTY_ID**) et que l’ID est déterminé par le paramètre spécifié juste après le paramètre *pszName* . Consultez AFXDISP. H pour plus d’informations sur ces macros. Les entrées **_id** doivent être placées à la fin de la table de dispatch. Elles affecteront la génération de **DISPID** automatique de la même façon qu’une version non **_id** de la macro (les **DISPID** s sont déterminées par position). Par exemple :

```cpp
BEGIN_DISPATCH_MAP(CDisp3DPoint, CCmdTarget)
    DISP_PROPERTY(CDisp3DPoint, "y", m_y, VT_I2)
    DISP_PROPERTY(CDisp3DPoint, "z", m_z, VT_I2)
    DISP_PROPERTY_ID(CDisp3DPoint, "x", 0x00020003, m_x, VT_I2)
END_DISPATCH_MAP()
```

MFC génère des DISPID pour la classe CDisp3DPoint comme suit :

```cpp
property X    (DISPID)0x00020003
property Y    (DISPID)0x00000002
property Z    (DISPID)0x00000001
```

La spécification d’un **DISPID** fixe est utile pour maintenir la compatibilité descendante avec une interface de dispatch précédemment existante, ou pour implémenter certaines méthodes ou propriétés définies par le système (généralement indiquées par un **DISPID** négatif, tel que la collection **DISPID_NEWENUM** ).

## <a name="retrieving-the-idispatch-interface-for-a-coleclientitem"></a>Récupération de l’interface IDispatch pour un COleClientItem

De nombreux serveurs prennent en charge l’automatisation dans leurs objets document, avec la fonctionnalité de serveur OLE. Pour accéder à cette interface d’automatisation, il est nécessaire d’accéder directement à la `COleClientItem::m_lpObject` variable membre. Le code ci-dessous récupère l' `IDispatch` interface pour un objet dérivé de `COleClientItem` . Vous pouvez inclure le code ci-dessous dans votre application si vous trouvez cette fonctionnalité nécessaire :

```cpp
LPDISPATCH CMyClientItem::GetIDispatch()
{
    ASSERT_VALID(this);
    ASSERT(m_lpObject != NULL);

    LPUNKNOWN lpUnk = m_lpObject;

    Run();      // must be running

    LPOLELINK lpOleLink = NULL;
    if (m_lpObject->QueryInterface(IID_IOleLink,
        (LPVOID FAR*)&lpOleLink) == NOERROR)
    {
        ASSERT(lpOleLink != NULL);
        lpUnk = NULL;
        if (lpOleLink->GetBoundSource(&lpUnk) != NOERROR)
        {
            TRACE0("Warning: Link is not connected!\n");
            lpOleLink->Release();
            return NULL;
        }
        ASSERT(lpUnk != NULL);
    }

    LPDISPATCH lpDispatch = NULL;
    if (lpUnk->QueryInterface(IID_IDispatch, &lpDispatch) != NOERROR)
    {
        TRACE0("Warning: does not support IDispatch!\n");
        return NULL;
    }

    ASSERT(lpDispatch != NULL);
    return lpDispatch;
}
```

L’interface de dispatch retournée par cette fonction peut ensuite être utilisée directement ou attachée à un `COleDispatchDriver` pour un accès de type sécurisé. Si vous l’utilisez directement, veillez à appeler son `Release` membre quand vous le faites avec le pointeur (le `COleDispatchDriver` destructeur effectue cette opération par défaut).

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
