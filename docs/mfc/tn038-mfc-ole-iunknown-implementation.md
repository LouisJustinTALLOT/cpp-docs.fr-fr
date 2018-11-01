---
title: 'TN038 : Implémentation IUnknown MFC-OLE'
ms.date: 06/28/2018
f1_keywords:
- vc.mfc.ole
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
ms.openlocfilehash: 0722ce294e6a088446b8ba681810cf3f7885f122
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571429"
---
# <a name="tn038-mfcole-iunknown-implementation"></a>TN038 : implémentation IUnknown MFC/OLE

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Au cœur d'OLE 2 se trouve COM ou « OLE Component Object Model ». COM définit une norme de communication entre les objets coopérants. Cela inclut les détails de présentation d'un « objet », notamment le mode de distribution des méthodes sur un objet. COM définit aussi une classe de base dont sont dérivées toutes les classes compatibles COM. Cette classe de base est [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown). Bien que le [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) interface est appelée une classe C++, COM n’est pas spécifique à un langage, il peut être implémenté en C, PASCAL ou tout autre langage prenant en charge la disposition binaire d’un objet COM.

OLE fait référence à toutes les classes dérivées de [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) en tant que « interfaces ». Cette distinction est importante, car une « interface » comme [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) s’accompagne d’aucune implémentation. Elle définit simplement le protocole de communication utilisé par les objets et non les détails de cette implémentation. Cela est raisonnable pour un système qui prévoit une flexibilité maximale. MFC a pour fonction d'implémenter un comportement par défaut pour les programmes MFC/C++.

Pour comprendre l’implémentation MFC de [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) vous devez d’abord comprendre ce que cette interface est. Une version simplifiée de [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) est défini ci-dessous :

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
> Certains détails nécessaires de la convention d’appel, tels que `__stdcall`, sont omis dans cette illustration.

Le [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref) et [version](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) fonctions membres de contrôlent la gestion de la mémoire de l’objet. COM utilise un système de comptage de références pour assurer le suivi des objets. Les objets ne sont jamais référencés directement comme en C++. Au lieu de cela, les objets COM sont toujours référencés au moyen d'un pointeur. Pour libérer l’objet lorsque le propriétaire est effectué à l’aide de son, l’objet [Release](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) membre est appelé (par opposition à l’utilisation de la suppression d’opérateur, comme vous pouvez la supprimer pour un objet C++ traditionnel). Le mécanisme de comptage de références autorise la gestion de plusieurs références à un même objet. Une implémentation de [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref) et [version](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) conserve un décompte de références sur l’objet, l’objet n’est pas supprimé tant que son décompte de références atteint zéro.

[AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref) et [version](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) sont assez simples à partir d’un point de vue d’implémentation. Voici une implémentation rudimentaire :

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

Le [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) la fonction membre est un peu plus intéressante. Il n’est pas très intéressant de disposer d’un objet dont les seules fonctions membres sont [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref) et [version](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) , il serait intéressant d’indiquer à l’objet pour effectuer d’autres choses que [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) fournit. C’est là où [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) est utile. Elle vous permet d'obtenir une « interface » différente sur le même objet. Ces interfaces sont dérivés habituellement de [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) et ajouter des fonctionnalités supplémentaires en ajoutant de nouvelles fonctions membres. Les interfaces COM ne font jamais déclarer de variables membres dans l'interface, et toutes les fonctions membres sont déclarées de façon purement virtuelle. Par exemple :

```cpp
class IPrintInterface : public IUnknown
{
public:
    virtual void PrintObject() = 0;
};
```

Pour obtenir une interface IPrintInterface si vous n’avez qu’un [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown), appelez [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) à l’aide de la `IID` de la `IPrintInterface`. Un `IID` est un nombre 128 bits qui identifie l'interface de manière unique. À chaque interface définie par vous-même ou par OLE correspond un `IID`. Si *pUnk* est un pointeur vers un [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) de l’objet, le code pour extraire une interface IPrintInterface peut être :

```cpp
IPrintInterface* pPrint = NULL;
if (pUnk->QueryInterface(IID_IPrintInterface, (void**)&pPrint) == NOERROR)
{
    pPrint->PrintObject();
    pPrint->Release();
    // release pointer obtained via QueryInterface
}
```

Cela paraît assez simple, mais comment implémenteriez-vous un objet prenant en charge les deux la mesure où IPrintInterface et [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) interface dans ce cas il est simple dans la mesure où IPrintInterface est directement dérivée de [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) — en implémentant IPrintInterface, [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) est automatiquement prise en charge. Exemple :

```cpp
class CPrintObj : public CPrintInterface
{
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj);
    virtual ULONG AddRef();
    virtual ULONG Release();
    virtual void PrintObject();
};
```

Les implémentations de [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref) et [version](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) serait exactement la même que ces implémentée ci-dessus. `CPrintObj::QueryInterface` ressemblent à ceci :

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

Comme vous pouvez le constater, si l'identificateur d'interface (IID) est reconnu, un pointeur est retourné vers l'objet ; sinon, une erreur se produit. Notez également que réussite [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) entraîne une implicite [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref). Bien entendu, vous devrez aussi implémenter CEditObj::Print. C’est simple parce que la mesure où IPrintInterface a été dérivée directement à partir de la [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) interface. Toutefois, si vous souhaitez prendre en charge deux interfaces différentes, toutes deux dérivées de [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown), considérez les éléments suivants :

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

Notez que la plupart de la [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) implémentation est placée dans la classe CEditPrintObj au lieu de dupliquer le code dans CEditPrintObj::CEditObj et CEditPrintObj::CPrintObj. Cela réduit la quantité de code et évite les bogues. Le point clé ici est qu’il est possible d’appeler à partir de l’interface IUnknown [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) à récupérer n’importe quelle interface, l’objet peut prendre en charge, et à partir de chacune de ces interfaces, il est possible de faire de même. Cela signifie que tous les [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) fonctions disponibles à partir de chaque interface doivent se comporter exactement la même façon. Pour que ces objets incorporés appellent l'implémentation dans l'« objet externe », un pointeur arrière est utilisée (m_pParent). Le pointeur m_pParent est initialisé dans le cadre du constructeur CEditPrintObj. Vous devez ensuite implémenter CEditPrintObj::CPrintObj::PrintObject, ainsi que CEditPrintObj::CEditObj::EditObject. Une certaine quantité de code a été ajoutée pour adjoindre une fonctionnalité permettant de modifier l'objet. Heureusement, il est assez rare que les interfaces aient une seule fonction membre (quoique cela puisse arriver). Dans ce cas, EditObject et PrintObject sont généralement combinés dans une interface unique.

Cela représente beaucoup d'explications et beaucoup de code pour un scénario aussi simple. Les classes MFC/OLE offrent une alternative plus simple. L'implémentation MFC utilise une technique similaire à la façon dont Windows inclut les messages dans un wrapper avec les tables des messages. Cette fonctionnalité est appelée *tables d’Interface* et est décrit dans la section suivante.

## <a name="mfc-interface-maps"></a>Tables d'interface MFC

MFC/OLE inclut une implémentation de « Tables d'interface » qui s'apparente aux « Tables des messages » et aux « Tables de dispatch » de MFC sur le plan du concept et de l'exécution. Les principales fonctionnalités des Tables d’interface de MFC sont les suivantes :

- Une implémentation standard de [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown), intégrée à la `CCmdTarget` classe.

- Maintenance du décompte de références, modifié par [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref) et [mise en production](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release)

- Implémentation de piloté par les données [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_))

Par ailleurs, les tables d’interface prennent en charge les fonctionnalités avancées suivantes :

- Prise en charge de la création d'objets COM agrégeables.

- Prise en charge de l'utilisation d'objets d'agrégation dans l'implémentation d'un objet COM.

- L'implémentation est hookable et extensible.

Pour plus d’informations sur l’agrégation, consultez le [agrégation](/windows/desktop/com/aggregation) rubrique.

La prise en charge des tables d'interface de MFC est ancrée dans la classe `CCmdTarget`. `CCmdTarget` «*a un*» référence nombre ainsi que toutes les fonctions membres associées le [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) implémentation (le décompte de références est par exemple dans `CCmdTarget`). Pour créer une classe qui prenne en charge OLE COM, vous devez faire dériver une classe de `CCmdTarget` et utiliser diverses macros, ainsi que des fonctions membres de `CCmdTarget` pour implémenter les interfaces souhaitées. L'implémentation de MFC utilise des classes imbriquées pour définir chaque implémentation d'interface de façon très similaire à l'exemple ci-dessus. Cela est facilité par une implémentation standard de l'interface IUnknown et par un certain nombre de macros qui permettent d'éliminer une partie du code répétitif.

## <a name="interface-map-basics"></a>Principes fondamentaux des tables d'interface

### <a name="to-implement-a-class-using-mfcs-interface-maps"></a>Pour implémenter une classe en utilisant des tables d'interface de MFC

1. Faites dériver une classe directement ou indirectement de `CCmdTarget`.

2. Utilisez la fonction `DECLARE_INTERFACE_MAP` dans la définition de la classe dérivée.

3. Pour chaque interface que vous souhaitez prendre en charge, utilisez les macros BEGIN_INTERFACE_PART et END_INTERFACE_PART dans la définition de classe.

4. Dans le fichier d’implémentation, utilisez les macros BEGIN_INTERFACE_MAP et END_INTERFACE_MAP pour définir le mappage d’interface de la classe.

5. Pour chaque IID pris en charge, utilisez l’interface_part (macro) entre les macros BEGIN_INTERFACE_MAP et END_INTERFACE_MAP pour mapper cet IID à une « partie » spécifique de votre classe.

6. Implémentez chacune des classes imbriquées qui représentent les interfaces que vous prenez en charge.

7. Utilisez la macro METHOD_PROLOGUE pour accéder au parent, `CCmdTarget`-objet dérivé.

8. [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref), [version](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release), et [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) peut déléguer le `CCmdTarget` implémentation de ces fonctions (`ExternalAddRef`, `ExternalRelease`, et `ExternalQueryInterface`).

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

La déclaration ci-dessus crée une classe dérivée de `CCmdTarget`. Le declare_interface_map (macro) indique à l’infrastructure que cette classe possède une carte d’interface personnalisée. En outre, les macros BEGIN_INTERFACE_PART et END_INTERFACE_PART des classes imbriquées, dans ce cas, définissez avec les noms CEditObj et CPrintObj (le X sert seulement à différencier les classes imbriquées des classes globales qui commencent par « C » et l’interface de classes qui Commencez par « I »). Deux membres imbriqués de ces classes sont créés : m_CEditObj et m_CPrintObj, respectivement. Les macros déclarent automatiquement la [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref), [version](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release), et [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) fonctions ; par conséquent vous ne déclarer les fonctions spécifiques à cette interface : EditObject et PrintObject (la macro OLE STDMETHOD est utilisé afin que **_stdcall** et les mots clés virtuels soient fournis en fonction de la plateforme cible).

Pour implémenter la table d'interface pour cette classe :

```cpp
BEGIN_INTERFACE_MAP(CPrintEditObj, CCmdTarget)
    INTERFACE_PART(CPrintEditObj, IID_IPrintInterface, PrintObj)
    INTERFACE_PART(CPrintEditObj, IID_IEditInterface, EditObj)
END_INTERFACE_MAP()
```

Cela a pour effet de connecter l'IID d'IID_IPrintInterface à m_CPrintObj et IID_IEditInterface à m_CEditObj, respectivement. Le `CCmdTarget` implémentation de [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) (`CCmdTarget::ExternalQueryInterface`) utilise cette table pour retourner des pointeurs vers m_CPrintObj et m_CEditObj quand demandé. Il n'est pas nécessaire d'inclure une entrée pour `IID_IUnknown` ; l'infrastructure utilisera la première interface de la table (en l'occurrence, m_CPrintObj) quand `IID_IUnknown` sera demandé.

Bien que la macro BEGIN_INTERFACE_PART déclarée automatiquement le [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref), [version](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) et [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) fonctions pour vous, vous devez toujours les implémenter :

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

L'implémentation pour CEditPrintObj::CPrintObj serait similaire aux définitions ci-dessus de CEditPrintObj::CEditObj. Bien qu'il soit possible de créer une macro qui permettrait de générer automatiquement ces fonctions (comme c'était le cas à un stade plus précoce du développement de MFC/OLE), il devient difficile de définir des points d'arrêt quand une macro génère plus d'une ligne de code. C'est pour cette raison que ce code est développé manuellement.

En utilisant l'implémentation des tables des messages de l'infrastructure, il y a un certain nombre de choses qu'il n'était pas nécessaire de faire :

- implémenter QueryInterface,

- implémenter AddRef et Release,

- déclarer l'une ou l'autre de ces méthodes intégrées dans les deux interfaces.

Par ailleurs, l'infrastructure utilise des tables des messages en interne. Vous pouvez ainsi dériver d'une classe d'infrastructure, disons `COleServerDoc`, qui prend déjà en charge certaines interfaces et fournit des remplacements ou des ajouts aux interfaces fournies par l'infrastructure. Si cela est possible, c'est parce que l'infrastructure prend entièrement en charge l'héritage d'une table d'interface à partir d'une classe de base. C’est pourquoi BEGIN_INTERFACE_MAP prend comme deuxième paramètre, le nom de la classe de base.

> [!NOTE]
> En général, il n'est pas possible de réutiliser les implémentations intégrées des interfaces OLE de MFC en héritant simplement de la spécialisation incorporée de ces interfaces de la version MFC. Ce n’est pas possible, car l’utilisation de la macro METHOD_PROLOGUE pour accéder au contenant `CCmdTarget`-implique de l’objet dérivé un *décalage fixe* de l’objet incorporé à partir de la `CCmdTarget`-objet dérivé. Cela signifie, par exemple, que vous ne pouvez pas faire dériver un XMyAdviseSink incorporé de l'implémentation MFC dans `COleClientItem::XAdviseSink`, car XAdviseSink s'attend à un certain décalage entre sa position et le sommet de l'objet `COleClientItem`.

> [!NOTE]
> Vous pouvez cependant déléguer à l'implémentation MFC pour toutes les fonctions qui doivent constituer le comportement par défaut de MFC. Cette opération est effectuée dans l'implémentation MFC d'`IOleInPlaceFrame` (XOleInPlaceFrame) dans la classe `COleFrameHook` (elle délègue à m_xOleInPlaceUIWindow pour de nombreuses fonctions). Cette conception a été choisie pour réduire, au moment de l'exécution, la taille des objets qui implémentent de nombreuses interfaces ; elle évite de recourir à un pointeur de retour (à la manière dont était utilisée la méthode m_pParent dans la section précédente).

### <a name="aggregation-and-interface-maps"></a>Agrégation et tables d'interface

En plus de prendre en charge les objets COM autonomes, MFC prend aussi en charge l'agrégation. Agrégation proprement dite est un sujet trop complexe pour discuter ici ; reportez-vous à la [agrégation](/windows/desktop/com/aggregation) rubrique pour plus d’informations sur l’agrégation. Dans cette note, nous nous bornerons à décrire la prise en charge de l'agrégation intégrée à l'infrastructure et aux tables d'interface.

Il existe deux façons d'utiliser l'agrégation : soit en utilisant un objet COM qui prenne en charge l'agrégation, soit en implémentant un objet qui puisse être agrégé par un autre. Autrement dit, cela consiste à « utiliser un objet d'agrégation » et à « rendre un objet agrégeable ». MFC prend en charge les deux méthodes.

### <a name="using-an-aggregate-object"></a>Utilisation d'un objet d'agrégation

Pour utiliser un objet d'agrégation, il doit exister un moyen de lier l'agrégation au mécanisme QueryInterface. En d'autres termes, l'objet d'agrégation doit se comporter comme s'il s'agissait d'une part native de votre objet. Par conséquent, comment est ce lien dans le mécanisme de mappage d’interface de MFC en plus de l’interface_part (macro), où un objet imbriqué est mappé à un IID, vous pouvez également déclarer un objet d’agrégation dans le cadre de votre `CCmdTarget` classe dérivée. Pour ce faire, la macro INTERFACE_AGGREGATE est utilisée. Cela vous permet de spécifier une variable membre (qui doit être un pointeur vers un [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) ou classe dérivée), lequel doit être intégré dans le mécanisme de mappage d’interface. Si le pointeur n’est pas NULL lorsque `CCmdTarget::ExternalQueryInterface` est appelée, le framework appelle automatiquement l’objet d’agrégation [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) fonction membre, si le `IID` demandé ne fait pas partie des natif `IID`s prise en charge par le `CCmdTarget` objet lui-même.

#### <a name="to-use-the-interfaceaggregate-macro"></a>Pour utiliser la macro INTERFACE_AGGREGATE

1. Déclarez une variable membre (une interface `IUnknown*`) qui contiendra un pointeur vers l'objet d'agrégation.

2. Incluez une macro INTERFACE_AGGREGATE dans votre carte d’interface, ce qui fait référence à la variable de membre par son nom.

3. À un moment donné (généralement dans le cadre de `CCmdTarget::OnCreateAggregates`), initialisez la variable membre avec une valeur différente de NULL.

Exemple :

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

La variable m_lpAggrInner est initialisée dans le constructeur avec la valeur NULL. Le framework ignore une variable de membre NULL dans l’implémentation par défaut de [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)). `OnCreateAggregates` offre un moyen efficace de créer véritablement vos objets d'agrégation. Vous devrez l'appeler explicitement si vous créez l'objet en dehors de l'implémentation MFC de `COleObjectFactory`. L'intérêt de créer des agrégations dans `CCmdTarget::OnCreateAggregates` et d'utiliser `CCmdTarget::GetControllingUnknown` vous apparaîtra évident quand nous aborderons la question de la création d'objets agrégeables.

Cette technique mettre à la disposition de votre objet toutes les interfaces prises en charge par l'objet d'agrégation, ainsi que ses interfaces natives. Si vous voulez seulement un sous-ensemble des interfaces prises en charge par l'agrégation, vous pouvez substituer `CCmdTarget::GetInterfaceHook`. Cela vous permet de très bas niveau hookability, similaire à [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)). Habituellement, les utilisateurs choisissent toutes les interfaces prises en charge par l'agrégation.

### <a name="making-an-object-implementation-aggregatable"></a>Rendre une implémentation d'objet agrégeable

Pour un objet soit agrégeable, l’implémentation de [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref), [version](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release), et [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) doivent déléguer à un « inconnu de contrôle ». En d’autres termes, pour qu’elle soit la partie de l’objet, elle doit déléguer [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref), [version](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release), et [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) à un autre objet, également dérivé [ IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown). Cet « inconnu de contrôle » est fourni à l'objet au moment où il est créé. Autrement dit, il est fourni à l'implémentation de `COleObjectFactory`. Dans la mesure où cette implémentation s'accompagne de quelques frais généraux, ce qui n'est pas souhaitable dans certains cas, MFC en fait une option. Pour rendre un objet agrégeable, vous devez appeler `CCmdTarget::EnableAggregation` à partir du constructeur de l'objet.

Si l'objet utilise également des agrégations, vous devez aussi veiller à passer le bon « inconnu de contrôle » aux objets d'agrégation. En général, ce [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) pointeur est transmis à l’objet lors de la création de l’agrégat. Par exemple, le paramètre pUnkOuter est l'« inconnu de contrôle » pour les objets créés avec `CoCreateInstance`. Le pointeur « inconnu de contrôle » adéquat peut être récupéré en appelant `CCmdTarget::GetControllingUnknown`. Cependant, la valeur retournée par cette fonction n'est pas valide dans le cadre du constructeur. C'est pourquoi il est conseillé de créer ses agrégations uniquement dans le cadre d'une substitution de `CCmdTarget::OnCreateAggregates`, où la valeur de retour de `GetControllingUnknown` est fiable, même si elle a été créée à partir de l'implémentation de `COleObjectFactory`.

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

Appelez cette fonction dans votre implémentation d'IUnknown::Release pour chaque interface que votre classe implémente. La valeur de retour indique le nouveau nombre de références au niveau de l'objet. Si l'objet est agrégée, cette fonction appelle l'« IUnknown de contrôle » au lieu de manipuler le nombre de références locales.

### <a name="declareinterfacemap--macro-description"></a>Description de la macro DECLARE_INTERFACE_MAP

```cpp
DECLARE_INTERFACE_MAP
```

#### <a name="remarks"></a>Notes

Utilisez cette macro dans une classe dérivée de `CCmdTarget` qui sera dotée d'une table d'interface. Utilisé à peu près la même façon que DECLARE_MESSAGE_MAP. L'appel de cette macro doit être placé dans la définition de la classe, généralement dans un fichier d'en-tête (.H). Une classe avec DECLARE_INTERFACE_MAP doit définir la table d’interface dans le fichier d’implémentation (. (CPP) avec les macros BEGIN_INTERFACE_MAP et END_INTERFACE_MAP.

### <a name="begininterfacepart-and-endinterfacepart--macro-descriptions"></a>Description des macros BEGIN_INTERFACE_PART et END_INTERFACE_PART

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

Pour chaque interface que votre classe doit implémenter, vous devez disposer d’une paire BEGIN_INTERFACE_PART et END_INTERFACE_PART. Ces macros définissent une classe locale dérivée de l'interface OLE que vous définissez, ainsi qu'une variable membre incorporée de cette classe. Le [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref), [version](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release), et [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) membres sont déclarés automatiquement. Vous devez inclure les déclarations pour les autres fonctions membres qui font partie de l’interface implémentée (ces déclarations sont placées entre les macros BEGIN_INTERFACE_PART et END_INTERFACE_PART).

Le *iface* argument est l’interface OLE que vous souhaitez implémenter, par exemple `IAdviseSink`, ou `IPersistStorage` (ou votre propre interface personnalisée).

Le *localClass* argument est le nom de la classe locale qui sera définie. Un « X » est automatiquement ajouté au nom. L'emploi de cette convention d'affectation de noms vise à éviter les conflits avec les classes globales de même nom. En outre, le nom du membre incorporé, le même que le *localClass* , sauf qu’il est précédé de « m_x ».

Exemple :

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
> Les lignes commençant par `STDMETHOD`_ sont essentiellement copiés depuis OLE2. H et légèrement modifié. Le fait de les copier depuis OLE2. H permet de limiter des erreurs difficiles à corriger.

### <a name="begininterfacemap-and-endinterfacemap--macro-descriptions"></a>Description des macros BEGIN_INTERFACE_MAP et END_INTERFACE_MAP

```cpp
BEGIN_INTERFACE_MAP(theClass, baseClass)
END_INTERFACE_MAP
```

#### <a name="parameters"></a>Paramètres

*theClass*<br/>
Classe dans laquelle la table d'interface doit être définie.

*classe de base*<br/>
La classe à partir de laquelle *theClass* dérive.

#### <a name="remarks"></a>Notes

Les macros BEGIN_INTERFACE_MAP et END_INTERFACE_MAP sont utilisés dans le fichier d’implémentation pour définir véritablement la table d’interface. Pour chaque interface est implémentée, il existe un ou plusieurs appels de macro INTERFACE_PART. Pour chaque agrégat qui utilise la classe, il existe un appel de macro INTERFACE_AGGREGATE.

### <a name="interfacepart--macro-description"></a>Description de la macro INTERFACE_PART

```cpp
INTERFACE_PART(theClass, iid, localClass)
```

#### <a name="parameters"></a>Paramètres

*theClass*<br/>
Nom de la classe qui contient la table d'interface.

*IID*<br/>
`IID` qui doit être mappé à la classe incorporée.

*localClass*<br/>
Nom de la classe locale (sans le « X »).

#### <a name="remarks"></a>Notes

Cette macro est utilisée entre la macro BEGIN_INTERFACE_MAP et la macro END_INTERFACE_MAP pour chaque interface que votre objet prendra en charge. Il vous permet de mapper un IID à un membre de la classe indiquée par *theClass* et *localClass*. Le préfixe « m_x » est ajoutée à la *localClass* automatiquement. Notez que plusieurs `IID` peuvent être associés à un même membre. Cela s'avère très utile quand vous implémentez uniquement une interface « la plus dérivée » et que vous voulez aussi fournir toutes les interfaces intermédiaires. L'interface `IOleInPlaceFrameWindow` en constitue un bon exemple. Sa hiérarchie se présente comme suit :

```Hierarchy
IUnknown
    IOleWindow
        IOleUIWindow
            IOleInPlaceFrameWindow
```

Si un objet implémente `IOleInPlaceFrameWindow`, un client peut appeler `QueryInterface` sur n’importe quel de ces interfaces : `IOleUIWindow`, `IOleWindow`, ou [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown), outre l’interface « la plus dérivée » `IOleInPlaceFrameWindow` (celui vous sont en fait implémentation). Gérer cette situation, vous pouvez utiliser plusieurs interface_part (macro) pour mapper chaque interface de base pour le `IOleInPlaceFrameWindow` interface :

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

### <a name="interfacepart--macro-description"></a>Description de la macro INTERFACE_PART

```cpp
INTERFACE_AGGREGATE(theClass, theAggr)
```

#### <a name="parameters"></a>Paramètres

*theClass*<br/>
Nom de la classe qui contient la table d'interface.

*theAggr*<br/>
Nom de la variable membre qui doit être agrégée.

#### <a name="remarks"></a>Notes

Cette macro est utilisée pour indiquer à l'infrastructure que la classe utilise un objet d'agrégation. Elle doit apparaître entre les macros BEGIN_INTERFACE_PART et END_INTERFACE_PART. Un objet d’agrégation est un objet distinct, dérivé [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown). En utilisant un agrégat et la macro INTERFACE_AGGREGATE, vous pouvez apporter toutes les interfaces qui le prend en charge l’agrégation semble être directement pris en charge par l’objet. Le *theAggr* argument est simplement le nom d’une variable de membre de votre classe dérivée de [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) (directement ou indirectement). Toutes les macros INTERFACE_AGGREGATE doivent suivre les macros INTERFACE_PART lorsqu’elle est placée dans une table d’interface.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
