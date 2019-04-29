---
title: 'TN039 : Implémentation d’Automation MFC / OLE'
ms.date: 06/28/2018
f1_keywords:
- vc.mfc.ole
helpviewer_keywords:
- MFC, COM support
- IDispatch interface
- MFC, OLE DB and
- TN039
- Automation, MFC COM interface entry points
ms.assetid: 765fa3e9-dd54-4f08-9ad2-26e0546ff8b6
ms.openlocfilehash: cd6f8d681ef7e6517f2172ca6b22b13723a962fd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305487"
---
# <a name="tn039-mfcole-automation-implementation"></a>TN039 : Implémentation d’Automation MFC/OLE

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

## <a name="overview-of-ole-idispatch-interface"></a>Vue d’ensemble de l’Interface IDispatch de OLE

Le `IDispatch` interface est le moyen par lequel les applications exposent des méthodes et propriétés de sorte que les autres applications telles que Visual BASIC, ou d’autres langages, peuvent faire utiliser des fonctionnalités de l’application. La partie la plus importante de cette interface est le `IDispatch::Invoke` (fonction). MFC utilise « tables de dispatch » pour implémenter `IDispatch::Invoke`. La table de dispatch fournit les informations de mise en œuvre de MFC sur la disposition ou la « forme » de votre `CCmdTarget`-les classes dérivées, telles qu’il peut directement manipuler les propriétés de l’objet, ou appeler des fonctions au sein de votre objet pour satisfaire aux membres `IDispatch::Invoke` requêtes.

La plupart du temps, ClassWizard et MFC coopèrent pour masquer la plupart des détails de OLE automation pour les programmeurs d’applications. Le programmeur se concentre sur la véritable fonctionnalité d’exposer dans l’application et n’a pas à vous soucier de la plomberie sous-jacent.

Il existe des cas où il est nécessaire de comprendre ce que fait MFC dans les coulisses. Cette note répondront comment le framework assigne **DISPID**s aux fonctions membres et aux propriétés. Connaissances de l’algorithme de MFC utilise pour l’affectation **DISPID**s est nécessaire uniquement lorsque vous devez connaître les ID, comme lorsque vous créez une bibliothèque de types « » pour les objets de votre application.

## <a name="mfc-dispid-assignment"></a>Affectation de MFC DISPID

Bien que l’utilisateur final d’automatisation (Visual Basic utilisateur, par exemple), voit les noms réels de l’automatisation activé propriétés et méthodes dans leur code (par exemple, obj. ShowWindow), l’implémentation de `IDispatch::Invoke` ne reçoit pas les noms réels. Pour des raisons de l’optimisation, il reçoit un **DISPID**, qui est 32 bits « magic cookie » qui décrit la méthode ou propriété est accessible. Ces **DISPID** valeurs sont retournées à partir de la `IDispatch` implémentation via une autre méthode, appelée `IDispatch::GetIDsOfNames`. Une application cliente automation appellera `GetIDsOfNames` une fois pour chaque membre ou la propriété qu’elle souhaite accéder et les mettre en cache pour les appels ultérieurs à `IDispatch::Invoke`. De cette façon, la recherche de chaîne coûteux est uniquement effectuée qu’une fois par utilisation de l’objet, au lieu d’une fois par `IDispatch::Invoke` appeler.

MFC détermine le **DISPID**s pour chaque méthode et la propriété selon deux choses :

- La distance du haut de la table de dispatch (1 relative)

- La distance de la table de dispatch de la classe la plus dérivée (0 relatif)

Le **DISPID** est divisé en deux parties. Le **LOWORD** de la **DISPID** contient le premier composant, la distance du haut de la table de dispatch. Le **HIWORD** contient la distance à partir de la classe la plus dérivée. Exemple :

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

Comme vous pouvez le voir, il existe deux classes, qui présentent les interfaces OLE automation. Une de ces classes est dérivée de l’autre et par conséquent, tire parti des fonctionnalités de la classe de base, y compris la partie d’automation OLE (« x » et « y » propriétés dans ce cas).

MFC génère **DISPID**s pour classe CDispPoint comme suit :

```cpp
property X    (DISPID)0x00000001
property Y    (DISPID)0x00000002
```

Étant donné que les propriétés ne sont pas dans une classe de base, le **HIWORD** de la **DISPID** est toujours égale à zéro (la distance à partir de la classe la plus dérivée pour CDispPoint est égal à zéro).

MFC génère **DISPID**s pour classe CDisp3DPoint comme suit :

```cpp
property Z    (DISPID)0x00000001
property X    (DISPID)0x00010001
property Y    (DISPID)0x00010002
```

La propriété Z est donnée un **DISPID** avec un zéro **HIWORD** dans la mesure où il est défini dans la classe qui expose les propriétés, CDisp3DPoint. Étant donné que les propriétés X et Y sont définies dans une classe de base, le **HIWORD** de la **DISPID** est 1, étant donné que la classe dans laquelle ces propriétés sont définies est à une distance d’une dérivation à partir de la classe la plus dérivée.

> [!NOTE]
> Le **LOWORD** est toujours déterminé par la position dans le mappage, même s’il existe des entrées dans la carte avec explicite **DISPID** (voir la section suivante pour plus d’informations sur la **_ID** les versions de la `DISP_PROPERTY` et `DISP_FUNCTION` macros).

## <a name="advanced-mfc-dispatch-map-features"></a>Fonctionnalités de mappage de Dispatch MFC avancées

Il existe plusieurs autres fonctionnalités ClassWizard ne prenant pas en charge avec cette version de Visual C++. ClassWizard prend en charge `DISP_FUNCTION`, `DISP_PROPERTY`, et `DISP_PROPERTY_EX` qui définissent une méthode, propriété de variable de membre et propriété de fonction membre get/set, respectivement. Ces fonctionnalités sont généralement tout ce qui est nécessaire pour créer la plupart des serveurs automation.

Les macros supplémentaires suivantes peuvent être utilisées lorsque les macros ClassWizard pris en charge ne sont pas adéquates : `DISP_PROPERTY_NOTIFY`, et `DISP_PROPERTY_PARAM`.

## <a name="disppropertynotify--macro-description"></a>DISP_PROPERTY_NOTIFY : Description de la Macro

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    pszName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>Paramètres

*theClass*<br/>
Nom de la classe.

*pszName*<br/>
Nom externe de la propriété.

*memberName*<br/>
Nom de la variable de membre dans lequel la propriété est stockée.

*pfnAfterSet*<br/>
Nom de la fonction membre à appeler lorsque la propriété est modifiée.

*vtPropType*<br/>
Une valeur qui spécifie le type de propriété.

### <a name="remarks"></a>Notes

Cette macro est similaire à DISP_PROPERTY, à ceci près qu’elle accepte un argument supplémentaire. L’argument supplémentaire, *pfnAfterSet,* doit être une fonction membre qui ne retourne rien et n’accepte aucun paramètre, « void OnPropertyNotify() ». Elle sera appelée **après** la variable de membre a été modifiée.

## <a name="disppropertyparam--macro-description"></a>DISP_PROPERTY_PARAM : Description de la Macro

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

*theClass*<br/>
Nom de la classe.

*pszName*<br/>
Nom externe de la propriété.

*memberGet*<br/>
Nom de la fonction de membre utilisée pour obtenir la propriété.

*memberSet*<br/>
Nom de la fonction membre permet de définir la propriété.

*vtPropType*<br/>
Une valeur qui spécifie le type de propriété.

*vtsParams*<br/>
Une chaîne d’espace séparées VTS_ pour chaque paramètre.

### <a name="remarks"></a>Notes

Beaucoup comme la macro DISP_PROPERTY_EX, cette macro définit une propriété accédée avec des fonctions membres Get et Set distinctes. Cette macro, toutefois, vous permet de spécifier une liste de paramètres pour la propriété. Cela est utile pour implémenter des propriétés qui sont indexées ou paramétrées par d’autres moyens. Les paramètres sont toujours placés en premier, suivie de la nouvelle valeur pour la propriété. Exemple :

```cpp
DISP_PROPERTY_PARAM(CMyObject, "item", GetItem, SetItem, VT_DISPATCH, VTS_I2 VTS_I2)
```

correspondrait pour obtenir et définir des fonctions membres :

```cpp
LPDISPATCH CMyObject::GetItem(short row, short col)
void CMyObject::SetItem(short row, short col, LPDISPATCH newValue)
```

## <a name="dispxxxxid--macro-descriptions"></a>DISP_XXXX_ID : Descriptions de Macro

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

*theClass*<br/>
Nom de la classe.

*pszName*<br/>
Nom externe de la propriété.

*dispid*<br/>
Le DISPID fixe pour la propriété ou méthode.

*pfnGet*<br/>
Nom de la fonction de membre utilisée pour obtenir la propriété.

*pfnSet*<br/>
Nom de la fonction membre permet de définir la propriété.

*memberName*<br/>
Le nom de la variable membre pour mapper à la propriété

*vtPropType*<br/>
Une valeur qui spécifie le type de propriété.

*vtsParams*<br/>
Une chaîne d’espace séparées VTS_ pour chaque paramètre.

### <a name="remarks"></a>Notes

Ces macros permettent de spécifier un **DISPID** au lieu de laisser MFC automatiquement attribuer un. Ces macros d’avancées ont les mêmes noms sauf cet ID est ajouté au nom de la macro (par exemple, **DISP_PROPERTY_ID**) et l’ID est déterminé par le paramètre spécifié juste après le *pszName* paramètre. Consultez AFXDISP. H pour plus d’informations sur ces macros. Le **_ID** entrées doivent être placées à la fin de la table de dispatch. Ils affectent l’automatique **DISPID** génération de la même façon en tant que non -**_ID** serait de version de la macro (le **DISPID**s sont déterminées par la position). Exemple :

```cpp
BEGIN_DISPATCH_MAP(CDisp3DPoint, CCmdTarget)
    DISP_PROPERTY(CDisp3DPoint, "y", m_y, VT_I2)
    DISP_PROPERTY(CDisp3DPoint, "z", m_z, VT_I2)
    DISP_PROPERTY_ID(CDisp3DPoint, "x", 0x00020003, m_x, VT_I2)
END_DISPATCH_MAP()
```

MFC génère DISPID pour la classe CDisp3DPoint comme suit :

```cpp
property X    (DISPID)0x00020003
property Y    (DISPID)0x00000002
property Z    (DISPID)0x00000001
```

En spécifiant un fixe **DISPID** est utile pour assurer la compatibilité descendante pour une interface de dispatch existe déjà, ou pour implémenter certains les méthodes définies par le système ou les propriétés (généralement indiqué par une valeur négative  **DISPID**, telles que la **DISPID_NEWENUM** collection).

## <a name="retrieving-the-idispatch-interface-for-a-coleclientitem"></a>Récupération de l’Interface IDispatch pour un COleClientItem

Nombre de serveurs prendra en charge d’automation au sein de leurs objets de document, ainsi que les fonctionnalités de serveur OLE. Pour accéder à cette interface automation, il est nécessaire pour accéder directement à la `COleClientItem::m_lpObject` variable membre. Le code ci-dessous récupère le `IDispatch` pour un objet dérivé de l’interface `COleClientItem`. Si vous trouvez cette fonctionnalité nécessaire, vous pouvez inclure le code ci-dessous dans votre application :

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

L’interface de dispatch retourné à partir de cette fonction peut ensuite être utilisée directement ou attachée à un `COleDispatchDriver` pour l’accès de type sécurisé. Si vous utilisez directement, assurez-vous que vous appelez son `Release` membre quand via le pointeur (le `COleDispatchDriver` destructeur le fait par défaut).

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
