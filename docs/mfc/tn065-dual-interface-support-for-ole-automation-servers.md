---
title: 'TN065 : Prise en charge de Interface double pour les serveurs Automation OLE | Microsoft Docs'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.ole
dev_langs:
- C++
helpviewer_keywords:
- dual interfaces [MFC], OLE Automation
- TN065 [MFC]
- ACDUAL sample [MFC]
- Automation servers [MFC], dual-interface support
ms.assetid: b5c8ed09-2f7f-483c-80fc-2a47ad896063
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 837149397ec45ebd8b41808b170b9f5e25146d6a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387690"
---
# <a name="tn065-dual-interface-support-for-ole-automation-servers"></a>TN065 : prise en charge d'une interface double pour les serveurs Automation OLE

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note indique comment ajouter la prise en charge d'interfaces doubles à un serveur Automation MFC. Le [ACDUAL](../visual-cpp-samples.md) exemple illustre la prise en charge de l’interface double, et l’exemple de code dans cette note provient de ACDUAL. Les macros décrites dans cette note, telles que DECLARE_DUAL_ERRORINFO, DUAL_ERRORINFO_PART et IMPLEMENT_DUAL_ERRORINFO, font partie de l’exemple ACDUAL et se trouve dans MFCDUAL. H.

## <a name="dual-interfaces"></a>Interfaces doubles

Bien que l'objet OLE Automation vous permet d'implémenter une interface `IDispatch`, une interface VTBL ou une double interface (qui comprend les deux), Microsoft recommande vivement d'implémenter des interfaces doubles pour tous les objets OLE Automation accessibles. Les interfaces doubles offrent d'importants avantages par rapport aux interfaces `IDispatch` uniquement ou uniquement VTBL :

- La liaison peut avoir lieu au moment de la compilation via l'interface VTBL, ou à l'aide de `IDispatch`.

- Les contrôleurs OLE Automation qui peuvent utiliser l'interface VTBL peuvent tirer parti de meilleures performances.

- Les contrôleurs OLE Automation existants qui utilisent l'interface `IDispatch` continuent à fonctionner.

- Il est plus facile d'appeler l'interface VTBL en C++.

- Les interfaces doubles sont requises pour la compatibilité avec les fonctionnalités de prise en charge des objets Visual Basic.

## <a name="adding-dual-interface-support-to-a-ccmdtarget-based-class"></a>Ajout de la prise en charge des interfaces doubles à une classe basée sur CCmdTarget

Une interface double n'est qu'une simple interface personnalisée dérivée de `IDispatch`. La méthode la plus simple pour implémenter la prise en charge des interfaces doubles dans une classe basée sur `CCmdTarget` consiste d'abord à implémenter l'interface de dispatch normale sur votre classe à l'aide de MFC et ClassWizard, puis à ajouter l'interface personnalisée ultérieurement. Dans la plupart des cas, l'implémentation de l'interface utilisateur personnalisée délègue simplement à l'implémentation `IDispatch` MFC.

D'abord, modifiez le fichier ODL pour que votre serveur définisse des interfaces pour les objets. Pour définir une interface double, vous devez utiliser une instruction Interface, au lieu de l'instruction ALTER `DISPINTERFACE` que les assistants Visual C++ génèrent. Plutôt que de supprimer l'instruction `DISPINTERFACE` existante, ajoutez une nouvelle instruction Interface. En conservant la forme `DISPINTERFACE`, vous pouvez continuer à utiliser ClassWizard pour ajouter des propriétés et des méthodes à votre objet, mais vous devez ajouter les propriétés et les méthodes équivalentes à votre instruction Interface.

Une instruction interface pour une interface double doit avoir le *OLEAUTOMATION* et *double* attributs et l’interface doivent être dérivé de `IDispatch`. Vous pouvez utiliser la [GUIDGEN](../visual-cpp-samples.md) exemple pour créer un **IID** pour l’interface double :

```IDL
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick
    oleautomation,
    dual
]
interface IDualAClick : IDispatch
    {
    };
```

Une fois que vous avez mis en place l'instruction Interface, commencez à ajouter les entrées des méthodes et des propriétés. Pour les interfaces doubles, vous devez réorganiser les listes de paramètres afin que vos méthodes et les fonctions d’accesseur de propriété dans l’interface double retournent un **HRESULT** et transmettre leurs valeurs de retour en tant que paramètres avec les attributs `[retval,out]`. N'oubliez pas que pour les propriétés, vous devez ajouter une fonction d'accesseur de lecture (`propget`) et d'écriture (`propput`) avec le même ID. Exemple :

```IDL
[propput, id(1)] HRESULT text([in] BSTR newText);
[propget, id(1)] HRESULT text([out, retval] BSTR* retval);
```

Après avoir défini vos méthodes et propriétés, vous devez ajouter une référence à l'instruction Interface dans l'instruction Coclass. Exemple :

```IDL
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]
coclass Document
{
    dispinterface IAClick;
    [default] interface IDualAClick;
};
```

Une fois votre fichier ODL mis à jour, utilisez le mécanisme de mappage d'interface de MFC pour définir une classe d'implémentation pour l'interface double dans votre classe d'objets et effectuer les entrées correspondantes dans le mécanisme `QueryInterface` de MFC. Vous avez besoin d'une entrée dans le bloc `INTERFACE_PART` pour chaque entrée dans l'instruction Interface de l'ODL, en plus des entrées valides pour une interface de dispatch. Chaque entrée ODL possédant le *propput* attribut requiert une fonction nommée `put_propertyname`. Chaque entrée avec la *propget* attribut requiert une fonction nommée `get_propertyname`.

Pour définir une classe d'implémentation pour votre interface double, ajoutez un bloc `DUAL_INTERFACE_PART` à la définition de classe d'objets. Exemple :

```cpp
BEGIN_DUAL_INTERFACE_PART(DualAClick, IDualAClick)
    STDMETHOD(put_text)(THIS_ BSTR newText);
    STDMETHOD(get_text)(THIS_ BSTR FAR* retval);
    STDMETHOD(put_x)(THIS_ short newX);
    STDMETHOD(get_x)(THIS_ short FAR* retval);
    STDMETHOD(put_y)(THIS_ short newY);
    STDMETHOD(get_y)(THIS_ short FAR* retval);
    STDMETHOD(put_Position)(THIS_ IDualAutoClickPoint FAR* newPosition);
    STDMETHOD(get_Position)(THIS_ IDualAutoClickPoint FAR* FAR* retval);
    STDMETHOD(RefreshWindow)(THIS);
    STDMETHOD(SetAllProps)(THIS_ short x, short y, BSTR text);
    STDMETHOD(ShowWindow)(THIS);
END_DUAL_INTERFACE_PART(DualAClick)
```

Se connecter l’interface double à MFC [QueryInterface](/windows/desktop/com/queryinterface--navigating-in-an-object) mécanisme, ajoutez un `INTERFACE_PART` entrée à la table d’interface :

```cpp
BEGIN_INTERFACE_MAP(CAutoClickDoc, CDocument)
    INTERFACE_PART(CAutoClickDoc, DIID_IAClick, Dispatch)
    INTERFACE_PART(CAutoClickDoc, IID_IDualAClick, DualAClick)
END_INTERFACE_MAP()
```

Ensuite, vous devez effectuer l'implémentation de l'interface. Dans la plupart des cas, vous pouvez déléguer à l'implémentation de l'interface `IDispatch` MFC existante. Exemple :

```cpp
STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::AddRef()
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalAddRef();
}

STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::Release()
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalRelease();
}

STDMETHODIMP CAutoClickDoc::XDualAClick::QueryInterface(
    REFIID iid,
    LPVOID* ppvObj)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalQueryInterface(&iid, ppvObj);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfoCount(
    UINT FAR* pctinfo)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);
    return lpDispatch->GetTypeInfoCount(pctinfo);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfo(
    UINT itinfo,
    LCID lcid,
    ITypeInfo FAR* FAR* pptinfo)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetTypeInfo(itinfo, lcid, pptinfo);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetIDsOfNames(
    REFIID riid,
    OLECHAR FAR* FAR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID FAR* rgdispid)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetIDsOfNames(riid, rgszNames, cNames, lcid, rgdispid);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::Invoke(
    DISPID dispidMember,
    REFIID riid,
    LCID lcid,
    WORD wFlags,
    DISPPARAMS FAR* pdispparams,
    VARIANT FAR* pvarResult,
    EXCEPINFO FAR* pexcepinfo,
    UINT FAR* puArgErr)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->Invoke(dispidMember, riid, lcid,
        wFlags, pdispparams, pvarResult, pexcepinfo, puArgErr);
}
```

Pour les méthodes et les fonctions d’accesseur de propriété de vos objets, vous devez effectuer l’implémentation. Les fonctions de méthodes et de propriétés peuvent généralement redéléguer aux méthodes générées par ClassWizard. Toutefois, si vous installez des propriétés pour accéder aux variables directement, vous devez écrire du code pour obtenir/placer la valeur dans la variable. Exemple :

```cpp
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    // MFC automatically converts from Unicode BSTR to
    // Ansi CString, if necessary...
    pThis->m_str = newText;
    return NOERROR;
}

STDMETHODIMP CAutoClickDoc::XDualAClick::get_text(BSTR* retval)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    // MFC automatically converts from Ansi CString to
    // Unicode BSTR, if necessary...
    pThis->m_str.SetSysString(retval);
    return NOERROR;
}
```

## <a name="passing-dual-interface-pointers"></a>Passage des pointeurs d'interface double

Le passage du pointeur d'interface double n'est pas simple, surtout si vous devez appeler `CCmdTarget::FromIDispatch`. `FromIDispatch` fonctionne uniquement sur les pointeurs `IDispatch` de MFC. Une méthode pour contourner ce point consiste à rechercher l'installation du pointeur `IDispatch` d'origine mis en place par MFC et de passer le pointeur aux fonctions qui en ont besoin. Exemple :

```
STDMETHODIMP CAutoClickDoc::XDualAClick::put_Position(
    IDualAutoClickPoint FAR* newPosition)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDisp = NULL;
    newPosition->QueryInterface(IID_IDispatch, (LPVOID*)&lpDisp);
    pThis->SetPosition(lpDisp);
    lpDisp->Release();
    return NOERROR;
}
```

Avant de retransmettre un pointeur via la méthode d'interface double, vous devrez peut-être le convertir à partir du pointeur `IDispatch` de MFC en pointeur d'interface double. Exemple :

```
STDMETHODIMP CAutoClickDoc::XDualAClick::get_Position(
    IDualAutoClickPoint FAR* FAR* retval)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDisp;
    lpDisp = pThis->GetPosition();
    lpDisp->QueryInterface(IID_IDualAutoClickPoint, (LPVOID*)retval);
    return NOERROR;
}
```

## <a name="registering-the-applications-type-library"></a>Inscription du type de bibliothèque de l'application

AppWizard ne génère pas de code pour enregistrer la bibliothèque de types d'une application serveur OLE Automation par le système. Lorsqu'il existe d'autres façons d'inscrire la bibliothèque de types, il est plus commode de faire en sorte que le registre de l'application enregistre la bibliothèque de types lorsqu'il met à jour ses informations de type OLE, c'est-à-dire chaque fois que l'application autonome est exécutée.

Pour inscrire la bibliothèque de types d'application chaque fois que l'application autonome est exécutée :

- Ajoutez AFXCTL.H à votre fichier d'en-tête includes standard, STDAFX.H, pour accéder à la définition de la fonction `AfxOleRegisterTypeLib`.

- Dans la fonction `InitInstance` de votre application, recherchez l'appel à `COleObjectFactory::UpdateRegistryAll`. Après cet appel, ajoutez un appel à `AfxOleRegisterTypeLib`, en spécifiant le **LIBID** correspondant à votre bibliothèque de types, ainsi que le nom de votre bibliothèque de types :

    ```cpp
    // When a server application is launched stand-alone, it is a good idea
    // to update the system registry in case it has been damaged.
    m_server.UpdateRegistry(OAT_DISPATCH_OBJECT);

    COleObjectFactory::UpdateRegistryAll();

    // DUAL_SUPPORT_START
        // Make sure the type library is registered or dual interface won't work.
        AfxOleRegisterTypeLib(AfxGetInstanceHandle(),
            LIBID_ACDual,
            _T("AutoClik.TLB"));
    // DUAL_SUPPORT_END
    ```

## <a name="modifying-project-build-settings-to-accommodate-type-library-changes"></a>Modification des paramètres de génération des projets pour tenir compte des changements de la bibliothèque de types ;

Pour modifier les paramètres de génération d’un projet afin qu’un fichier d’en-tête contenant **UUID** définitions est généré par MkTypLib à chaque fois que la bibliothèque de types est reconstruite :

1. Sur le **Build** menu, cliquez sur **paramètres**, puis sélectionnez le fichier ODL dans la liste des fichiers pour chaque configuration.

2. Cliquez sur le **OLE Types** onglet et spécifier un nom de fichier dans le **en-tête de sortie** champ nom de fichier. Utilisez un nom de fichier qui n'est pas déjà utilisé par votre projet, car MkTypLib remplacera un fichier déjà existant. Cliquez sur **OK** pour fermer la **paramètres de Build** boîte de dialogue.

Pour ajouter le **UUID** définitions à partir du fichier d’en-tête généré par MkTypLib à votre projet :

1. Inclut le fichier d'en-tête généré par MkTypLib dans le fichier d'en-tête includes standard, STDAFX.H.

2. Créez un fichier, INITIIDS.CPP, et ajoutez le à votre projet. Dans ce fichier, ajoutez votre fichier d'en-tête généré par MkTypLib après avoir inclus OLE2.H et INITGUID.H :

    ```cpp
    // initIIDs.c: defines IIDs for dual interfaces
    // This must not be built with precompiled header.
    #include <ole2.h>
    #include <initguid.h>
    #include "acdual.h"
    ```

3. Sur le **Build** menu, cliquez sur **paramètres**, puis sélectionnez INITIIDS. CPP à partir de la liste des fichiers pour chaque configuration.

4. Cliquez sur le **C++** , cliquez sur la catégorie **en-têtes précompilés**, puis sélectionnez le **ne pas à l’aide d’en-têtes précompilés** case d’option. Cliquez sur OK pour fermer la **paramètres de Build** boîte de dialogue.

## <a name="specifying-the-correct-object-class-name-in-the-type-library"></a>Spécification du nom de classe d'objets correct dans une bibliothèque de types

Les assistants fournis avec Visual C++ utilisent incorrectement le nom de classe d’implémentation pour spécifier la coclasse dans le fichier ODL du serveur pour les classes pouvant être créées par OLE. Si cette opération fonctionne, le nom de classe d'implémentation n'est probablement pas le nom de classe que vous souhaitez que les utilisateurs de votre objet utilisent. Pour spécifier le bon nom, ouvrez le fichier ODL, recherchez chaque instruction Coclass et remplacez le nom de classe d’implémentation par le nom externe correct.

Notez que lorsque l’instruction coclass est modifiée, les noms de variables de **CLSID**s dans le fichier d’en-tête généré par MkTypLib changent en conséquence. Vous devez mettre à jour votre code afin d'utiliser les nouveaux noms de variables.

## <a name="handling-exceptions-and-the-automation-error-interfaces"></a>Gestion des exceptions et des interfaces d'erreur Automation

Les méthodes et les fonctions d’accesseur de propriété de votre objet automation peuvent lever des exceptions. Si, par conséquent, vous devez les gérer dans votre implémentation d’interface double et passer des informations relatives à l’exception vers le contrôleur via l’interface de gestion des erreurs OLE Automation, `IErrorInfo`. Cette interface fournit des informations d'erreur détaillées et contextuelles à travers à la fois de `IDispatch` et des interfaces VTBL. Pour indiquer qu’un gestionnaire d’erreurs est disponible, vous devez implémenter le `ISupportErrorInfo` interface.

Pour illustrer le mécanisme de gestion des erreurs, supposez que les fonctions générées par ClassWizard permettant d'implémenter la prise en charge de la distribution (dispatch) standard lèvent des exceptions. L’implémentation MFC de `IDispatch::Invoke` généralement intercepte ces exceptions et les convertit en une structure EXCEPTINFO qui est retournée via le `Invoke` appeler. Toutefois, lorsque l'interface VTBL est utilisée, vous êtes chargé d'intercepter les exceptions vous-même. Voici un exemple de protection des méthodes d'interface double :

```cpp
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    TRY_DUAL(IID_IDualAClick)
    {
        // MFC automatically converts from Unicode BSTR to
        // Ansi CString, if necessary...
        pThis->m_str = newText;
        return NOERROR;
    }
    CATCH_ALL_DUAL
}
```

`CATCH_ALL_DUAL` prend soin de retourner un code d'erreur approprié lorsqu'une exception se produit. `CATCH_ALL_DUAL` Convertit une exception MFC dans à l’aide des informations de gestion des erreurs OLE Automation le `ICreateErrorInfo` interface. (Un exemple `CATCH_ALL_DUAL` macro se trouve dans le fichier MFCDUAL. H dans le [ACDUAL](../visual-cpp-samples.md) exemple. La fonction utilisée pour gérer les exceptions, `DualHandleException`, se trouve dans le fichier MFCDUAL.CPP.) `CATCH_ALL_DUAL` détermine le code d'erreur à retourner en fonction du type d'exception qui s'est produite :

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) : dans ce cas, `HRESULT` est construit en utilisant le code suivant :

    ```cpp
    hr = MAKE_HRESULT(SEVERITY_ERROR, FACILITY_ITF, (e->m_wCode + 0x200));
    ```

     Cela crée un `HRESULT` spécifique à l'interface qui a provoqué l'exception. Le code d'erreur est décalé de 0x200 pour éviter tout conflit avec les `HRESULT`définis par le système pour les interfaces OLE standard.

- [CMemoryException](../mfc/reference/cmemoryexception-class.md) : dans ce cas, `E_OUTOFMEMORY` est retournée.

- Toute autre exception - dans ce cas, `E_UNEXPECTED` est retournée.

Pour indiquer que le Gestionnaire d’erreurs OLE Automation est utilisé, vous devez également implémenter la `ISupportErrorInfo` interface.

Tout d’abord, ajoutez le code à votre définition de classe automation pour montrer qu’il prend en charge `ISupportErrorInfo`.

Ensuite, ajoutez le code au mappage d’interface de votre classe automation pour associer le `ISupportErrorInfo` classe d’implémentation de MFC `QueryInterface` mécanisme. Le `INTERFACE_PART` instruction correspond à la classe définie pour `ISupportErrorInfo`.

Enfin, implémentez la classe définie pour prendre en charge `ISupportErrorInfo`.

(Le [ACDUAL](../visual-cpp-samples.md) exemple contient trois macros aidant à effectuer ces trois étapes, `DECLARE_DUAL_ERRORINFO`, `DUAL_ERRORINFO_PART`, et `IMPLEMENT_DUAL_ERRORINFO`, toutes contenues dans MFCDUAL. H.)

L’exemple suivant implémente une classe définie pour prendre en charge `ISupportErrorInfo`. `CAutoClickDoc` est le nom de votre classe automation et `IID_IDualAClick` est la **IID** pour l’interface qui est la source des erreurs signalées par l’objet d’erreur OLE Automation :

```cpp
STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::AddRef()
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalAddRef();
}

STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::Release()
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalRelease();
}

STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::QueryInterface(
    REFIID iid,
    LPVOID* ppvObj)
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalQueryInterface(&iid, ppvObj);
}

STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::InterfaceSupportsErrorInfo(
    REFIID iid)
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return (iid == IID_IDualAClick) S_OK : S_FALSE;
}
```

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
