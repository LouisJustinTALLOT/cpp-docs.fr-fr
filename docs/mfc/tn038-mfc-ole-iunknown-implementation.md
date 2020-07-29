---
title: 'TN038 : implémentation de l’interface IUnknown OLE MFC'
ms.date: 06/28/2018
helpviewer_keywords:
- aggregation macros [MFC]
- COM interfaces, base interface
- IUnknown interface
- END_INTERFACE_MAP macro [MFC]
- TN038
- BEGIN_INTERFACE_PART macro [MFC]
- DECLARE_INTERFACE_MAP macro [MFC]
- BEGIN_INTERFACE_MAP macro [MFC]
- OLE [MFC], implementing IUnknown interface
- METHOD_PROLOGUE macro [MFC]
- STDMETHOD macro [MFC]
- END_INTERFACE_PART macro [MFC]
- INTERFACE_PART macro
ms.assetid: 19d946ba-beaf-4881-85c6-0b598d7f6f11
ms.openlocfilehash: 83166b32a20b8d24f748f85946caa01dbc76d4d0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230439"
---
# <a name="tn038-mfcole-iunknown-implementation"></a>TN038 : implémentation IUnknown MFC/OLE

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Au cœur d'OLE 2 se trouve COM ou « OLE Component Object Model ». COM définit une norme de communication entre les objets coopérants. Cela inclut les détails de présentation d'un « objet », notamment le mode de distribution des méthodes sur un objet. COM définit aussi une classe de base dont sont dérivées toutes les classes compatibles COM. Cette classe de base est [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown). Bien que l’interface [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) soit appelée classe C++, com n’est pas spécifique à un langage, elle peut être implémentée en C, en Pascal ou dans tout autre langage capable de prendre en charge la disposition binaire d’un objet com.

OLE fait référence à toutes les classes dérivées de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) en tant qu’interfaces. Il s’agit d’une distinction importante, car une « interface » telle que [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) ne s’accompagne d’aucune implémentation. Elle définit simplement le protocole de communication utilisé par les objets et non les détails de cette implémentation. Cela est raisonnable pour un système qui prévoit une flexibilité maximale. MFC a pour fonction d'implémenter un comportement par défaut pour les programmes MFC/C++.

Pour comprendre l’implémentation de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) dans MFC, vous devez d’abord comprendre ce qu’est cette interface. Une version simplifiée de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) est définie ci-dessous :

```cpp
class IUnknown
{
public:
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj) = 0;
    virtual ULONG AddRef() = 0;
    virtual ULONG Release() = 0;
};
```

> [!NOTE]
> Certains détails nécessaires de la Convention d’appel, tels que, **`__stdcall`** sont omis pour cette illustration.

Les fonctions membres [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) et [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) contrôlent la gestion de la mémoire de l’objet. COM utilise un système de comptage de références pour assurer le suivi des objets. Les objets ne sont jamais référencés directement comme en C++. Au lieu de cela, les objets COM sont toujours référencés au moyen d'un pointeur. Pour libérer l’objet une fois que le propriétaire a fini de l’utiliser, le membre [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) de l’objet est appelé (par opposition à l’utilisation de l’opérateur delete, comme c’est le cas pour un objet C++ traditionnel). Le mécanisme de comptage de références autorise la gestion de plusieurs références à un même objet. Une implémentation de [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) et [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) conserve un décompte de références sur l’objet : l’objet n’est pas supprimé tant que son décompte de références n’atteint pas zéro.

[AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) et [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) sont assez simples du point de vue de l’implémentation. Voici une implémentation rudimentaire :

```cpp
ULONG CMyObj::AddRef()
{
    return ++m_dwRef;
}

ULONG CMyObj::Release()
{
    if (--m_dwRef == 0)
    {
        delete this;
        return 0;
    }
    return m_dwRef;
}
```

La fonction membre [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) est un peu plus intéressante. Il n’est pas très intéressant d’avoir un objet dont les seules fonctions membres sont [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) et [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) ; il serait intéressant de dire à l’objet d’effectuer plus de choses que la fonction [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) . C’est là que [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) est utile. Elle vous permet d'obtenir une « interface » différente sur le même objet. Ces interfaces sont généralement dérivées de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) et ajoutent des fonctionnalités supplémentaires en ajoutant de nouvelles fonctions membres. Les interfaces COM ne font jamais déclarer de variables membres dans l'interface, et toutes les fonctions membres sont déclarées de façon purement virtuelle. Par exemple,

```cpp
class IPrintInterface : public IUnknown
{
public:
    virtual void PrintObject() = 0;
};
```

Pour obtenir un IPrintInterface si vous avez uniquement un [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown), appelez [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) à l’aide de l' `IID` du `IPrintInterface` . Un `IID` est un nombre 128 bits qui identifie l'interface de manière unique. À chaque interface définie par vous-même ou par OLE correspond un `IID`. Si *punk* est un pointeur vers un objet [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) , le code permettant de récupérer un IPrintInterface à partir de celui-ci peut être :

```cpp
IPrintInterface* pPrint = NULL;
if (pUnk->QueryInterface(IID_IPrintInterface, (void**)&pPrint) == NOERROR)
{
    pPrint->PrintObject();
    pPrint->Release();
    // release pointer obtained via QueryInterface
}
```

Cela semble relativement simple, mais comment implémentez-vous un objet prenant en charge à la fois l’interface IPrintInterface et [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) dans ce cas, c’est simple puisque le IPrintInterface est directement dérivé de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) , en implémentant IPrintInterface, [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) est pris en charge automatiquement. Par exemple :

```cpp
class CPrintObj : public CPrintInterface
{
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj);
    virtual ULONG AddRef();
    virtual ULONG Release();
    virtual void PrintObject();
};
```

Les implémentations de [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) et de [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) sont exactement les mêmes que celles implémentées ci-dessus. `CPrintObj::QueryInterface`devrait ressembler à ceci :

```cpp
HRESULT CPrintObj::QueryInterface(REFIID iid, void FAR* FAR* ppvObj)
{
    if (iid == IID_IUnknown || iid == IID_IPrintInterface)
    {
        *ppvObj = this;
        AddRef();
        return NOERROR;
    }
    return E_NOINTERFACE;
}
```

Comme vous pouvez le constater, si l'identificateur d'interface (IID) est reconnu, un pointeur est retourné vers l'objet ; sinon, une erreur se produit. Notez également qu’une [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) réussie aboutit à un [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)implicite. Bien entendu, vous devrez aussi implémenter CEditObj::Print. C’est simple, car le IPrintInterface a été directement dérivé de l’interface [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) . Toutefois, si vous souhaitez prendre en charge deux interfaces différentes, toutes deux dérivées de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown), tenez compte des éléments suivants :

```cpp
class IEditInterface : public IUnkown
{
public:
    virtual void EditObject() = 0;
};
```

Bien qu'il existe plusieurs façons d'implémenter une classe prenant en charge à la fois IEditInterface et IPrintInterface, notamment en utilisant l'héritage multiple C++, cette note se concentrera sur l'utilisation de classes imbriquées pour l'implémentation de cette fonctionnalité.

```cpp
class CEditPrintObj
{
public:
    CEditPrintObj();

    HRESULT QueryInterface(REFIID iid, void**);
    ULONG AddRef();
    ULONG Release();
    DWORD m_dwRef;

    class CPrintObj : public IPrintInterface
    {
    public:
        CEditPrintObj* m_pParent;
        virtual HRESULT QueryInterface(REFIID iid, void** ppvObj);
        virtual ULONG AddRef();
        virtual ULONG Release();
    } m_printObj;

    class CEditObj : public IEditInterface
    {
    public:
        CEditPrintObj* m_pParent;
        virtual ULONG QueryInterface(REFIID iid, void** ppvObj);
        virtual ULONG AddRef();
        virtual ULONG Release();
    } m_editObj;
};
```

L'intégralité de l'implémentation est incluse ci-dessous :

```cpp
CEditPrintObj::CEditPrintObj()
{
    m_editObj.m_pParent = this;
    m_printObj.m_pParent = this;
}

ULONG CEditPrintObj::AddRef()
{
    return ++m_dwRef;
}

CEditPrintObj::Release()
{
    if (--m_dwRef == 0)
    {
        delete this;
        return 0;
    }
    return m_dwRef;
}

HRESULT CEditPrintObj::QueryInterface(REFIID iid, void** ppvObj)
{
    if (iid == IID_IUnknown || iid == IID_IPrintInterface)
    {
        *ppvObj = &m_printObj;
        AddRef();
        return NOERROR;
    }
    else if (iid == IID_IEditInterface)
    {
        *ppvObj = &m_editObj;
        AddRef();
        return NOERROR;
    }
    return E_NOINTERFACE;
}

ULONG CEditPrintObj::CEditObj::AddRef()
{
    return m_pParent->AddRef();
}

ULONG CEditPrintObj::CEditObj::Release()
{
    return m_pParent->Release();
}

HRESULT CEditPrintObj::CEditObj::QueryInterface(REFIID iid, void** ppvObj)
{
    return m_pParent->QueryInterface(iid, ppvObj);
}

ULONG CEditPrintObj::CPrintObj::AddRef()
{
    return m_pParent->AddRef();
}

ULONG CEditPrintObj::CPrintObj::Release()
{
    return m_pParent->Release();
}

HRESULT CEditPrintObj::CPrintObj::QueryInterface(REFIID iid, void** ppvObj)
{
    return m_pParent->QueryInterface(iid, ppvObj);
}
```

Notez que la majeure partie de l’implémentation de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) est placée dans la classe CEditPrintObj au lieu de dupliquer le code dans CEditPrintObj :: CEditObj et CEditPrintObj :: CPrintObj. Cela réduit la quantité de code et évite les bogues. Le point clé ici est qu’à partir de l’interface IUnknown, il est possible d’appeler [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) pour récupérer toute interface que l’objet peut prendre en charge, et à partir de chacune de ces interfaces, il est possible de faire de même. Cela signifie que toutes les fonctions [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) disponibles à partir de chaque interface doivent se comporter exactement de la même façon. Pour que ces objets incorporés appellent l'implémentation dans l'« objet externe », un pointeur arrière est utilisée (m_pParent). Le pointeur m_pParent est initialisé dans le cadre du constructeur CEditPrintObj. Vous devez ensuite implémenter CEditPrintObj::CPrintObj::PrintObject, ainsi que CEditPrintObj::CEditObj::EditObject. Une certaine quantité de code a été ajoutée pour adjoindre une fonctionnalité permettant de modifier l'objet. Heureusement, il est assez rare que les interfaces aient une seule fonction membre (quoique cela puisse arriver). Dans ce cas, EditObject et PrintObject sont généralement combinés dans une interface unique.

Cela représente beaucoup d'explications et beaucoup de code pour un scénario aussi simple. Les classes MFC/OLE offrent une alternative plus simple. L'implémentation MFC utilise une technique similaire à la façon dont Windows inclut les messages dans un wrapper avec les tables des messages. Cette fonctionnalité est appelée *mappages d’interface* et est décrite dans la section suivante.

## <a name="mfc-interface-maps"></a>Tables d'interface MFC

MFC/OLE inclut une implémentation de « Tables d'interface » qui s'apparente aux « Tables des messages » et aux « Tables de dispatch » de MFC sur le plan du concept et de l'exécution. Les principales fonctionnalités des Tables d'interface de MFC sont les suivantes :

- Implémentation standard de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown), intégrée à la `CCmdTarget` classe.

- Maintenance du décompte de références, modifié par [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) et [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)

- Implémentation pilotée par les données de [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))

Par ailleurs, les tables d'interface prennent en charge les fonctionnalités avancées suivantes :

- Prise en charge de la création d'objets COM agrégeables.

- Prise en charge de l'utilisation d'objets d'agrégation dans l'implémentation d'un objet COM.

- L'implémentation est hookable et extensible.

Pour plus d’informations sur l’agrégation, consultez la rubrique [agrégation](/windows/win32/com/aggregation) .

La prise en charge des tables d'interface de MFC est ancrée dans la classe `CCmdTarget`. `CCmdTarget`«*possède un*» nombre de références, ainsi que toutes les fonctions membres associées à l’implémentation de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) (le nombre de références par exemple est dans `CCmdTarget` ). Pour créer une classe qui prenne en charge OLE COM, vous devez faire dériver une classe de `CCmdTarget` et utiliser diverses macros, ainsi que des fonctions membres de `CCmdTarget` pour implémenter les interfaces souhaitées. L'implémentation de MFC utilise des classes imbriquées pour définir chaque implémentation d'interface de façon très similaire à l'exemple ci-dessus. Cela est facilité par une implémentation standard de l'interface IUnknown et par un certain nombre de macros qui permettent d'éliminer une partie du code répétitif.

## <a name="interface-map-basics"></a>Principes fondamentaux des tables d'interface

### <a name="to-implement-a-class-using-mfcs-interface-maps"></a>Pour implémenter une classe en utilisant des tables d'interface de MFC

1. Faites dériver une classe directement ou indirectement de `CCmdTarget`.

2. Utilisez la fonction `DECLARE_INTERFACE_MAP` dans la définition de la classe dérivée.

3. Pour chaque interface que vous souhaitez prendre en charge, utilisez les macros BEGIN_INTERFACE_PART et END_INTERFACE_PART dans la définition de classe.

4. Dans le fichier d’implémentation, utilisez les macros BEGIN_INTERFACE_MAP et END_INTERFACE_MAP pour définir le mappage d’interface de la classe.

5. Pour chaque IID pris en charge, utilisez la macro INTERFACE_PART entre les macros BEGIN_INTERFACE_MAP et END_INTERFACE_MAP pour mapper cet IID à une « partie » spécifique de votre classe.

6. Implémentez chacune des classes imbriquées qui représentent les interfaces que vous prenez en charge.

7. Utilisez la macro METHOD_PROLOGUE pour accéder à l' `CCmdTarget` objet dérivé de parent.

8. [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)et [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) peuvent déléguer à l' `CCmdTarget` implémentation de ces fonctions ( `ExternalAddRef` , `ExternalRelease` et `ExternalQueryInterface` ).

L'exemple CPrintEditObj ci-dessus aurait pu être implémenté comme suit :

```cpp
class CPrintEditObj : public CCmdTarget
{
public:
    // member data and member functions for CPrintEditObj go here

// Interface Maps
protected:
    DECLARE_INTERFACE_MAP()

    BEGIN_INTERFACE_PART(EditObj, IEditInterface)
        STDMETHOD_(void, EditObject)();
    END_INTERFACE_PART(EditObj)

    BEGIN_INTERFACE_PART(PrintObj, IPrintInterface)
        STDMETHOD_(void, PrintObject)();
    END_INTERFACE_PART(PrintObj)
};
```

La déclaration ci-dessus crée une classe dérivée de `CCmdTarget`. La macro DECLARE_INTERFACE_MAP indique à l’infrastructure que cette classe aura un mappage d’interface personnalisé. En outre, les macros BEGIN_INTERFACE_PART et END_INTERFACE_PART définissent des classes imbriquées, dans ce cas avec les noms CEditObj et CPrintObj (le X est utilisé uniquement pour différencier les classes imbriquées des classes globales qui commencent par « C » et les classes d’interface qui commencent par « I »). Deux membres imbriqués de ces classes sont créés : m_CEditObj et m_CPrintObj, respectivement. Les macros déclarent automatiquement les fonctions [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)et [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) ; par conséquent, vous déclarez uniquement les fonctions spécifiques à cette interface : EditObject et PrintObject (la macro OLE STDMETHOD est utilisée afin que **_stdcall** et les mots clés virtuels soient fournis en fonction de la plateforme cible).

Pour implémenter la table d'interface pour cette classe :

```cpp
BEGIN_INTERFACE_MAP(CPrintEditObj, CCmdTarget)
    INTERFACE_PART(CPrintEditObj, IID_IPrintInterface, PrintObj)
    INTERFACE_PART(CPrintEditObj, IID_IEditInterface, EditObj)
END_INTERFACE_MAP()
```

Cela a pour effet de connecter l'IID d'IID_IPrintInterface à m_CPrintObj et IID_IEditInterface à m_CEditObj, respectivement. L' `CCmdTarget` implémentation de [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) ( `CCmdTarget::ExternalQueryInterface` ) utilise ce mappage pour retourner des pointeurs vers m_CPrintObj et m_CEditObj lorsqu’il est demandé. Il n'est pas nécessaire d'inclure une entrée pour `IID_IUnknown` ; l'infrastructure utilisera la première interface de la table (en l'occurrence, m_CPrintObj) quand `IID_IUnknown` sera demandé.

Même si la macro BEGIN_INTERFACE_PART a automatiquement déclaré les fonctions [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) et [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) , vous devez tout de même les implémenter :

```cpp
ULONG FAR EXPORT CEditPrintObj::XEditObj::AddRef()
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    return pThis->ExternalAddRef();
}

ULONG FAR EXPORT CEditPrintObj::XEditObj::Release()
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    return pThis->ExternalRelease();
}

HRESULT FAR EXPORT CEditPrintObj::XEditObj::QueryInterface(
    REFIID iid,
    void FAR* FAR* ppvObj)
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    return (HRESULT)pThis->ExternalQueryInterface(&iid, ppvObj);
}

void FAR EXPORT CEditPrintObj::XEditObj::EditObject()
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    // code to "Edit" the object, whatever that means...
}
```

L'implémentation pour CEditPrintObj::CPrintObj serait similaire aux définitions ci-dessus de CEditPrintObj::CEditObj. Bien qu'il soit possible de créer une macro qui permettrait de générer automatiquement ces fonctions (comme c'était le cas à un stade plus précoce du développement de MFC/OLE), il devient difficile de définir des points d'arrêt quand une macro génère plus d'une ligne de code. C’est pour cette raison que ce code est développé manuellement.

En utilisant l'implémentation des tables des messages de l'infrastructure, il y a un certain nombre de choses qu'il n'était pas nécessaire de faire :

- implémenter QueryInterface,

- implémenter AddRef et Release,

- déclarer l'une ou l'autre de ces méthodes intégrées dans les deux interfaces.

Par ailleurs, l'infrastructure utilise des tables des messages en interne. Vous pouvez ainsi dériver d'une classe d'infrastructure, disons `COleServerDoc`, qui prend déjà en charge certaines interfaces et fournit des remplacements ou des ajouts aux interfaces fournies par l'infrastructure. Si cela est possible, c'est parce que l'infrastructure prend entièrement en charge l'héritage d'une table d'interface à partir d'une classe de base. C’est la raison pour laquelle BEGIN_INTERFACE_MAP prend comme deuxième paramètre le nom de la classe de base.

> [!NOTE]
> En général, il n'est pas possible de réutiliser les implémentations intégrées des interfaces OLE de MFC en héritant simplement de la spécialisation incorporée de ces interfaces de la version MFC. Cela n’est pas possible, car l’utilisation de la macro METHOD_PROLOGUE pour obtenir l’accès à l' `CCmdTarget` objet dérivé de contenant implique un *décalage fixe* de l’objet incorporé de l' `CCmdTarget` objet dérivé de. Cela signifie, par exemple, que vous ne pouvez pas faire dériver un XMyAdviseSink incorporé de l'implémentation MFC dans `COleClientItem::XAdviseSink`, car XAdviseSink s'attend à un certain décalage entre sa position et le sommet de l'objet `COleClientItem`.

> [!NOTE]
> Vous pouvez cependant déléguer à l'implémentation MFC pour toutes les fonctions qui doivent constituer le comportement par défaut de MFC. Cette opération est effectuée dans l'implémentation MFC d'`IOleInPlaceFrame` (XOleInPlaceFrame) dans la classe `COleFrameHook` (elle délègue à m_xOleInPlaceUIWindow pour de nombreuses fonctions). Cette conception a été choisie pour réduire, au moment de l'exécution, la taille des objets qui implémentent de nombreuses interfaces ; elle évite de recourir à un pointeur de retour (à la manière dont était utilisée la méthode m_pParent dans la section précédente).

### <a name="aggregation-and-interface-maps"></a>Agrégation et tables d'interface

En plus de prendre en charge les objets COM autonomes, MFC prend aussi en charge l'agrégation. L’agrégation elle-même est trop complexe pour aborder ici. reportez-vous à la rubrique [agrégation](/windows/win32/com/aggregation) pour plus d’informations sur l’agrégation. Dans cette note, nous nous bornerons à décrire la prise en charge de l'agrégation intégrée à l'infrastructure et aux tables d'interface.

Il existe deux façons d'utiliser l'agrégation : soit en utilisant un objet COM qui prenne en charge l'agrégation, soit en implémentant un objet qui puisse être agrégé par un autre. Autrement dit, cela consiste à « utiliser un objet d'agrégation » et à « rendre un objet agrégeable ». MFC prend en charge les deux méthodes.

### <a name="using-an-aggregate-object"></a>Utilisation d'un objet d'agrégation

Pour utiliser un objet d'agrégation, il doit exister un moyen de lier l'agrégation au mécanisme QueryInterface. En d'autres termes, l'objet d'agrégation doit se comporter comme s'il s'agissait d'une part native de votre objet. Donc, comment cela s’attache-t-il au mécanisme de mappage d’interface de MFC en plus de la macro INTERFACE_PART, où un objet imbriqué est mappé à un IID, vous pouvez également déclarer un objet d’agrégation dans le cadre de votre `CCmdTarget` classe dérivée. Pour ce faire, la macro INTERFACE_AGGREGATE est utilisée. Cela vous permet de spécifier une variable membre (qui doit être un pointeur vers un [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) ou une classe dérivée), qui doit être intégrée dans le mécanisme de mappage d’interface. Si le pointeur n’est pas NULL lorsque `CCmdTarget::ExternalQueryInterface` est appelé, l’infrastructure appelle automatiquement la fonction membre [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) de l’objet d’agrégation, si le `IID` demandé n’est pas l’un des natifs `IID` pris en charge par l' `CCmdTarget` objet lui-même.

#### <a name="to-use-the-interface_aggregate-macro"></a>Pour utiliser la macro INTERFACE_AGGREGATE

1. Déclarez une variable membre (une interface `IUnknown*`) qui contiendra un pointeur vers l'objet d'agrégation.

2. Incluez une macro INTERFACE_AGGREGATE dans votre mappage d’interface, qui fait référence à la variable membre par nom.

3. À un moment donné (généralement dans le cadre de `CCmdTarget::OnCreateAggregates`), initialisez la variable membre avec une valeur différente de NULL.

Par exemple :

```cpp
class CAggrExample : public CCmdTarget
{
public:
    CAggrExample();

protected:
    LPUNKNOWN m_lpAggrInner;
    virtual BOOL OnCreateAggregates();

    DECLARE_INTERFACE_MAP()
    // "native" interface part macros may be used here
};

CAggrExample::CAggrExample()
{
    m_lpAggrInner = NULL;
}

BOOL CAggrExample::OnCreateAggregates()
{
    // wire up aggregate with correct controlling unknown
    m_lpAggrInner = CoCreateInstance(CLSID_Example,
        GetControllingUnknown(), CLSCTX_INPROC_SERVER,
        IID_IUnknown, (LPVOID*)&m_lpAggrInner);

    if (m_lpAggrInner == NULL)
        return FALSE;
    // optionally, create other aggregate objects here
    return TRUE;
}

BEGIN_INTERFACE_MAP(CAggrExample, CCmdTarget)
    // native "INTERFACE_PART" entries go here
    INTERFACE_AGGREGATE(CAggrExample, m_lpAggrInner)
END_INTERFACE_MAP()
```

La variable m_lpAggrInner est initialisée dans le constructeur avec la valeur NULL. L’infrastructure ignore une variable membre NULL dans l’implémentation par défaut de [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)). `OnCreateAggregates` offre un moyen efficace de créer véritablement vos objets d'agrégation. Vous devrez l'appeler explicitement si vous créez l'objet en dehors de l'implémentation MFC de `COleObjectFactory`. L'intérêt de créer des agrégations dans `CCmdTarget::OnCreateAggregates` et d'utiliser `CCmdTarget::GetControllingUnknown` vous apparaîtra évident quand nous aborderons la question de la création d'objets agrégeables.

Cette technique mettre à la disposition de votre objet toutes les interfaces prises en charge par l'objet d'agrégation, ainsi que ses interfaces natives. Si vous voulez seulement un sous-ensemble des interfaces prises en charge par l'agrégation, vous pouvez substituer `CCmdTarget::GetInterfaceHook`. Cela vous permet de disposer d’un niveau de raccordement très bas, similaire à [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)). Habituellement, les utilisateurs choisissent toutes les interfaces prises en charge par l'agrégation.

### <a name="making-an-object-implementation-aggregatable"></a>Rendre une implémentation d'objet agrégeable

Pour qu’un objet soit regroupable, l’implémentation de [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)et [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) doit déléguer à un « Control Unknown ». En d’autres termes, pour qu’elle fasse partie de l’objet, elle doit déléguer [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)et [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) à un autre objet, également dérivé de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown). Cet « inconnu de contrôle » est fourni à l'objet au moment où il est créé. Autrement dit, il est fourni à l'implémentation de `COleObjectFactory`. Dans la mesure où cette implémentation s'accompagne de quelques frais généraux, ce qui n'est pas souhaitable dans certains cas, MFC en fait une option. Pour rendre un objet agrégeable, vous devez appeler `CCmdTarget::EnableAggregation` à partir du constructeur de l'objet.

Si l'objet utilise également des agrégations, vous devez aussi veiller à passer le bon « inconnu de contrôle » aux objets d'agrégation. En général, ce pointeur [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) est passé à l’objet lors de la création de l’agrégat. Par exemple, le paramètre pUnkOuter est l'« inconnu de contrôle » pour les objets créés avec `CoCreateInstance`. Le pointeur « inconnu de contrôle » adéquat peut être récupéré en appelant `CCmdTarget::GetControllingUnknown`. Cependant, la valeur retournée par cette fonction n'est pas valide dans le cadre du constructeur. C'est pourquoi il est conseillé de créer ses agrégations uniquement dans le cadre d'une substitution de `CCmdTarget::OnCreateAggregates`, où la valeur de retour de `GetControllingUnknown` est fiable, même si elle a été créée à partir de l'implémentation de `COleObjectFactory`.

De même, il est important que l'objet manipule le nombre de références approprié lors de l'ajout ou de la libération de nombres de références artificiels. Pour vous assurer que c'est le cas, appelez toujours `ExternalAddRef` et `ExternalRelease` au lieu de `InternalRelease` et `InternalAddRef`. Il est rare d'appeler `InternalRelease` ou `InternalAddRef` sur une classe qui prend en charge l'agrégation.

## <a name="reference-material"></a>Documents de référence

L'utilisation avancée d'OLE, qui consiste notamment à définir vos propres interfaces ou à substituer l'implémentation par l'infrastructure des interfaces OLE, nécessite l'utilisation du mécanisme de table d'interface sous-jacent.

Cette section décrit chaque macro, ainsi que les API utilisées pour implémenter ces fonctionnalités avancées.

### <a name="ccmdtargetenableaggregation--function-description"></a>Description de la fonction CCmdTarget::EnableAggregation

```cpp
void EnableAggregation();
```

#### <a name="remarks"></a>Notes

Appelez cette fonction dans le constructeur de la classe dérivée si vous souhaitez prendre en charge l'agrégation OLE pour les objets de ce type. Elle prépare une implémentation spéciale d'IUnknown qui est nécessaire aux objets agrégeables.

### <a name="ccmdtargetexternalqueryinterface--function-description"></a>Description de la fonction CCmdTarget::ExternalQueryInterface

```cpp
DWORD ExternalQueryInterface(
    const void FAR* lpIID,
    LPVOIDFAR* ppvObj
);
```

#### <a name="parameters"></a>Paramètres

*lpIID*<br/>
Pointeur lointain vers un IID (premier argument à destination de QueryInterface)

*ppvObj*<br/>
Pointeur vers une interface IUnknown* (deuxième argument à destination de QueryInterface)

#### <a name="remarks"></a>Notes

Appelez cette fonction dans votre implémentation d'IUnknown pour chaque interface que votre classe implémente. Cette fonction assure l'implémentation standard pilotée par des données de QueryInterface en s'appuyant sur la table d'interface de votre objet. Il est nécessaire d'effectuer une conversation de type (transtypage) de la valeur de retour en HRESULT. Si l'objet est agrégée, cette fonction appelle l'« IUnknown de contrôle » au lieu d'utiliser la table d'interface locale.

### <a name="ccmdtargetexternaladdref--function-description"></a>Description de la fonction CCmdTarget::ExternalAddRef

```cpp
DWORD ExternalAddRef();
```

#### <a name="remarks"></a>Notes

Appelez cette fonction dans votre implémentation d'IUnknown::AddRef pour chaque interface que votre classe implémente. La valeur de retour est le nouveau nombre de références au niveau de l'objet CCmdTarget. Si l'objet est agrégée, cette fonction appelle l'« IUnknown de contrôle » au lieu de manipuler le nombre de références locales.

### <a name="ccmdtargetexternalrelease--function-description"></a>Description de la fonction CCmdTarget::ExternalRelease

```cpp
DWORD ExternalRelease();
```

#### <a name="remarks"></a>Notes

Appelez cette fonction dans votre implémentation d’IUnknown::Release pour chaque interface que votre classe implémente. La valeur de retour indique le nouveau nombre de références au niveau de l'objet. Si l'objet est agrégée, cette fonction appelle l'« IUnknown de contrôle » au lieu de manipuler le nombre de références locales.

### <a name="declare_interface_map--macro-description"></a>Description de la macro DECLARE_INTERFACE_MAP

```cpp
DECLARE_INTERFACE_MAP
```

#### <a name="remarks"></a>Notes

Utilisez cette macro dans une classe dérivée de `CCmdTarget` qui sera dotée d'une table d'interface. Utilisé à peu près de la même façon que DECLARE_MESSAGE_MAP. L'appel de cette macro doit être placé dans la définition de la classe, généralement dans un fichier d'en-tête (.H). Une classe avec DECLARE_INTERFACE_MAP doit définir le mappage d’interface dans le fichier d’implémentation (. CPP) avec les macros BEGIN_INTERFACE_MAP et END_INTERFACE_MAP.

### <a name="begin_interface_part-and-end_interface_part--macro-descriptions"></a>Description des macros BEGIN_INTERFACE_PART et END_INTERFACE_PART

```cpp
BEGIN_INTERFACE_PART(localClass, iface);
END_INTERFACE_PART(localClass)
```

#### <a name="parameters"></a>Paramètres

*localClass*<br/>
Nom de la classe qui implémente l'interface

*iface*<br/>
Nom de l'interface que cette classe implémente

#### <a name="remarks"></a>Notes

Pour chaque interface que votre classe doit implémenter, vous devez avoir une paire BEGIN_INTERFACE_PART et END_INTERFACE_PART. Ces macros définissent une classe locale dérivée de l'interface OLE que vous définissez, ainsi qu'une variable membre incorporée de cette classe. Les membres [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)et [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) sont déclarés automatiquement. Vous devez inclure les déclarations des autres fonctions membres qui font partie de l’interface implémentée (ces déclarations sont placées entre les macros BEGIN_INTERFACE_PART et END_INTERFACE_PART).

L’argument *iface* est l’interface OLE que vous souhaitez implémenter, par exemple `IAdviseSink` , ou `IPersistStorage` (ou votre propre interface personnalisée).

L’argument *localClass* est le nom de la classe locale qui sera définie. Un « X » est automatiquement ajouté au nom. L'emploi de cette convention d'affectation de noms vise à éviter les conflits avec les classes globales de même nom. En outre, le nom du membre incorporé, identique au nom *localClass* , sauf qu’il est préfixé par’m_x'.

Par exemple :

```cpp
BEGIN_INTERFACE_PART(MyAdviseSink, IAdviseSink)
    STDMETHOD_(void, OnDataChange)(LPFORMATETC, LPSTGMEDIUM);
    STDMETHOD_(void, OnViewChange)(DWORD, LONG);
    STDMETHOD_(void, OnRename)(LPMONIKER);
    STDMETHOD_(void, OnSave)();
    STDMETHOD_(void, OnClose)();
END_INTERFACE_PART(MyAdviseSink)
```

définit une classe locale appelée XMyAdviseSink dérivée d'IAdviseSink, ainsi qu'un membre de la classe dans laquelle il est déclaré sous le nom m_xMyAdviseSink.Note :

> [!NOTE]
> Les lignes commençant par `STDMETHOD` _ sont essentiellement copiées à partir de OLE2. H et modifié légèrement. Le fait de les copier depuis OLE2. H permet de limiter des erreurs difficiles à corriger.

### <a name="begin_interface_map-and-end_interface_map--macro-descriptions"></a>Description des macros BEGIN_INTERFACE_MAP et END_INTERFACE_MAP

```cpp
BEGIN_INTERFACE_MAP(theClass, baseClass)
END_INTERFACE_MAP
```

#### <a name="parameters"></a>Paramètres

*Les*<br/>
Classe dans laquelle la table d'interface doit être définie.

*baseClass*<br/>
Classe à partir de laquelle dérive *les* .

#### <a name="remarks"></a>Notes

Les macros BEGIN_INTERFACE_MAP et END_INTERFACE_MAP sont utilisées dans le fichier d’implémentation pour définir réellement le mappage d’interface. Pour chaque interface implémentée, il existe un ou plusieurs INTERFACE_PART appel de macro. Pour chaque agrégat utilisé par la classe, il existe un INTERFACE_AGGREGATE appel de macro.

### <a name="interface_part--macro-description"></a>Description de la macro INTERFACE_PART

```cpp
INTERFACE_PART(theClass, iid, localClass)
```

#### <a name="parameters"></a>Paramètres

*Les*<br/>
Nom de la classe qui contient la table d'interface.

*vaut*<br/>
`IID` qui doit être mappé à la classe incorporée.

*localClass*<br/>
Nom de la classe locale (sans le « X »).

#### <a name="remarks"></a>Notes

Cette macro est utilisée entre la macro BEGIN_INTERFACE_MAP et la macro END_INTERFACE_MAP pour chaque interface que votre objet prend en charge. Elle vous permet de mapper un IID à un membre de la classe indiquée par *les* et *localClass*. Le’m_x’sera automatiquement ajouté au *localClass* . Notez que plusieurs `IID` peuvent être associés à un même membre. Cela s'avère très utile quand vous implémentez uniquement une interface « la plus dérivée » et que vous voulez aussi fournir toutes les interfaces intermédiaires. L'interface `IOleInPlaceFrameWindow` en constitue un bon exemple. Sa hiérarchie se présente comme suit :

```Hierarchy
IUnknown
    IOleWindow
        IOleUIWindow
            IOleInPlaceFrameWindow
```

Si un objet implémente `IOleInPlaceFrameWindow` , un client peut `QueryInterface` sur l’une de ces interfaces : `IOleUIWindow` , `IOleWindow` ou [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown), en plus de l’interface « la plus dérivée » `IOleInPlaceFrameWindow` (celle que vous implémentez réellement). Pour gérer cela, vous pouvez utiliser plusieurs macros de INTERFACE_PART pour mapper chacune et chaque interface de base à l' `IOleInPlaceFrameWindow` interface :

dans le fichier de définition de classe :

```cpp
BEGIN_INTERFACE_PART(CMyFrameWindow, IOleInPlaceFrameWindow)
```

dans le fichier d'implémentation de classe :

```cpp
BEGIN_INTERFACE_MAP(CMyWnd, CFrameWnd)
    INTERFACE_PART(CMyWnd, IID_IOleWindow, MyFrameWindow)
    INTERFACE_PART(CMyWnd, IID_IOleUIWindow, MyFrameWindow)
    INTERFACE_PART(CMyWnd, IID_IOleInPlaceFrameWindow, MyFrameWindow)
END_INTERFACE_MAP
```

L'infrastructure gère l'interface IUnknown, car elle est toujours nécessaire.

### <a name="interface_part--macro-description"></a>Description de la macro INTERFACE_PART

```cpp
INTERFACE_AGGREGATE(theClass, theAggr)
```

#### <a name="parameters"></a>Paramètres

*Les*<br/>
Nom de la classe qui contient la table d'interface.

*theAggr*<br/>
Nom de la variable membre qui doit être agrégée.

#### <a name="remarks"></a>Notes

Cette macro est utilisée pour indiquer à l'infrastructure que la classe utilise un objet d'agrégation. Il doit apparaître entre les macros BEGIN_INTERFACE_PART et END_INTERFACE_PART. Un objet d’agrégation est un objet distinct, dérivé de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown). En utilisant un agrégat et la macro INTERFACE_AGGREGATE, vous pouvez faire en sorte que toutes les interfaces prises en charge par l’agrégat apparaissent comme étant directement prises en charge par l’objet. L’argument *theAggr* est simplement le nom d’une variable membre de votre classe qui est dérivée de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) (directement ou indirectement). Toutes les macros INTERFACE_AGGREGATE doivent suivre les macros INTERFACE_PARTes lorsqu’elles sont placées dans une carte d’interface.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
