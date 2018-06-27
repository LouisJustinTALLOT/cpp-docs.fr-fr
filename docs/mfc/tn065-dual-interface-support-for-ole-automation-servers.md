---
title: 'TN065 : Prise en charge de Interface double pour les serveurs Automation OLE | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: b066ac483de127e0ce469cf8aaf24991ae5f6ef8
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953036"
---
# <a name="tn065-dual-interface-support-for-ole-automation-servers"></a>TN065 : prise en charge d'une interface double pour les serveurs Automation OLE
> [!NOTE]
>  La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.  
  
 Cette note indique comment ajouter la prise en charge d'interfaces doubles à un serveur Automation MFC. Le [ACDUAL](../visual-cpp-samples.md) exemple illustre la prise en charge de l’interface double, et l’exemple de code dans cette note provient de ACDUAL. Les macros décrits dans cette note, telles que DECLARE_DUAL_ERRORINFO, DUAL_ERRORINFO_PART et IMPLEMENT_DUAL_ERRORINFO, font partie de l’exemple ACDUAL et sont accessibles dans MFCDUAL. H.  
  
## <a name="dual-interfaces"></a>Interfaces doubles  
 Bien que l'objet OLE Automation vous permet d'implémenter une interface `IDispatch`, une interface VTBL ou une double interface (qui comprend les deux), Microsoft recommande vivement d'implémenter des interfaces doubles pour tous les objets OLE Automation accessibles. Les interfaces doubles offrent d'importants avantages par rapport aux interfaces `IDispatch` uniquement ou uniquement VTBL :  
  
-   La liaison peut avoir lieu au moment de la compilation via l'interface VTBL, ou à l'aide de `IDispatch`.  
  
-   Les contrôleurs OLE Automation qui peuvent utiliser l'interface VTBL peuvent tirer parti de meilleures performances.  
  
-   Les contrôleurs OLE Automation existants qui utilisent l'interface `IDispatch` continuent à fonctionner.  
  
-   Il est plus facile d'appeler l'interface VTBL en C++.  
  
-   Les interfaces doubles sont requises pour la compatibilité avec les fonctionnalités de prise en charge des objets Visual Basic.  
  
## <a name="adding-dual-interface-support-to-a-ccmdtarget-based-class"></a>Ajout de la prise en charge des interfaces doubles à une classe basée sur CCmdTarget  
 Une interface double n'est qu'une simple interface personnalisée dérivée de `IDispatch`. La méthode la plus simple pour implémenter la prise en charge des interfaces doubles dans une classe basée sur `CCmdTarget` consiste d'abord à implémenter l'interface de dispatch normale sur votre classe à l'aide de MFC et ClassWizard, puis à ajouter l'interface personnalisée ultérieurement. Dans la plupart des cas, l'implémentation de l'interface utilisateur personnalisée délègue simplement à l'implémentation `IDispatch` MFC.  
  
 D'abord, modifiez le fichier ODL pour que votre serveur définisse des interfaces pour les objets. Pour définir une interface double, vous devez utiliser une instruction Interface, au lieu de l'instruction ALTER `DISPINTERFACE` que les assistants Visual C++ génèrent. Plutôt que de supprimer l'instruction `DISPINTERFACE` existante, ajoutez une nouvelle instruction Interface. En conservant la forme `DISPINTERFACE`, vous pouvez continuer à utiliser ClassWizard pour ajouter des propriétés et des méthodes à votre objet, mais vous devez ajouter les propriétés et les méthodes équivalentes à votre instruction Interface.  
  
 Une instruction interface pour une interface double doit avoir le *OLEAUTOMATION* et *double* attributs et l’interface doivent être dérivé de `IDispatch`. Vous pouvez utiliser la [GUIDGEN](../visual-cpp-samples.md) exemple pour créer un **IID** pour l’interface double :  
  
```  
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick  
    oleautomation, 
    dual 
]  
interface IDualAClick : IDispatch  
 {  
 };  
```  
  
 Une fois que vous avez mis en place l'instruction Interface, commencez à ajouter les entrées des méthodes et des propriétés. Pour les interfaces doubles, vous devez réorganiser les listes de paramètres afin que vos méthodes et les fonctions d’accesseur de propriété de l’interface double retournent un **HRESULT** et transmettent les valeurs de retournés en tant que paramètres avec les attributs `[retval,out]`. N'oubliez pas que pour les propriétés, vous devez ajouter une fonction d'accesseur de lecture (`propget`) et d'écriture (`propput`) avec le même ID. Exemple :  
  
```  
[propput,
    id(1)] HRESULT text([in] BSTR newText);

[propget,
    id(1)] HRESULT text([out,
    retval] BSTR* retval);
```  
  
 Après avoir défini vos méthodes et propriétés, vous devez ajouter une référence à l'instruction Interface dans l'instruction Coclass. Exemple :  
  
```  
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]  
coclass Document  
{  
    dispinterface IAClick;  
 [default] interface IDualAClick;  
};  
```  
  
 Une fois votre fichier ODL mis à jour, utilisez le mécanisme de mappage d'interface de MFC pour définir une classe d'implémentation pour l'interface double dans votre classe d'objets et effectuer les entrées correspondantes dans le mécanisme `QueryInterface` de MFC. Vous avez besoin d'une entrée dans le bloc `INTERFACE_PART` pour chaque entrée dans l'instruction Interface de l'ODL, en plus des entrées valides pour une interface de dispatch. Chaque entrée ODL possédant le *propput* attribut a besoin d’une fonction nommée `put_propertyname`. Chaque entrée avec le *propget* attribut a besoin d’une fonction nommée `get_propertyname`.  
  
 Pour définir une classe d'implémentation pour votre interface double, ajoutez un bloc `DUAL_INTERFACE_PART` à la définition de classe d'objets. Exemple :  
  
```  
BEGIN_DUAL_INTERFACE_PART(DualAClick,
    IDualAClick)  
    STDMETHOD(put_text)(THIS_ BSTR newText);

    STDMETHOD(get_text)(THIS_ BSTR FAR* retval);

    STDMETHOD(put_x)(THIS_ short newX);

    STDMETHOD(get_x)(THIS_ short FAR* retval);

    STDMETHOD(put_y)(THIS_ short newY);

    STDMETHOD(get_y)(THIS_ short FAR* retval);

    STDMETHOD(put_Position)(THIS_ IDualAutoClickPoint FAR* newPosition);

    STDMETHOD(get_Position)(THIS_ IDualAutoClickPoint FAR* FAR* retval);

    STDMETHOD(RefreshWindow)(THIS);

 STDMETHOD(SetAllProps)(THIS_ short x,
    short y,
    BSTR text);

    STDMETHOD(ShowWindow)(THIS);

END_DUAL_INTERFACE_PART(DualAClick) 
```  
  
 Pour connecter l’interface double à MFC [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms687230) mécanisme, ajoutez un `INTERFACE_PART` entrée à la table d’interface :  
  
```  
BEGIN_INTERFACE_MAP(CAutoClickDoc,
    CDocument)  
    INTERFACE_PART(CAutoClickDoc,
    DIID_IAClick,
    Dispatch)  
    INTERFACE_PART(CAutoClickDoc,
    IID_IDualAClick,
    DualAClick)  
END_INTERFACE_MAP()  
```  
  
 Ensuite, vous devez effectuer l'implémentation de l'interface. Dans la plupart des cas, vous pouvez déléguer à l'implémentation de l'interface `IDispatch` MFC existante. Exemple :  
  
```  
STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::AddRef()  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    return pThis->ExternalAddRef();

}  
STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::Release()  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    return pThis->ExternalRelease();

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::QueryInterface(
    REFIID iid,
    LPVOID* ppvObj)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    return pThis->ExternalQueryInterface(&iid,
    ppvObj);

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfoCount(
    UINT FAR* pctinfo)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);

    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetTypeInfoCount(pctinfo);

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfo(
    UINT itinfo,
    LCID lcid,
    ITypeInfo FAR* FAR* pptinfo)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);

    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetTypeInfo(itinfo,
    lcid,
    pptinfo);

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::GetIDsOfNames(
    REFIID riid,
    OLECHAR FAR* FAR* rgszNames,
    UINT cNames,  
    LCID lcid,
    DISPID FAR* rgdispid)   
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);

    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetIDsOfNames(riid,
    rgszNames,
    cNames,   
    lcid,
    rgdispid);

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
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);

    ASSERT(lpDispatch != NULL);

    return lpDispatch->Invoke(dispidMember,
    riid,
    lcid,  
    wFlags,
    pdispparams,
    pvarResult,  
    pexcepinfo,
    puArgErr);

}  
```  
  
 Pour les méthodes et les fonctions d’accesseur de propriété de vos objets, vous devez effectuer l’implémentation. Les fonctions de méthodes et de propriétés peuvent généralement redéléguer aux méthodes générées par ClassWizard. Toutefois, si vous installez des propriétés pour accéder aux variables directement, vous devez écrire du code pour obtenir/placer la valeur dans la variable. Exemple :  
  
```  
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick) *// MFC automatically converts from Unicode BSTR to *// Ansi CString,
    if necessary...  
    pThis->m_str = newText;  
    return NOERROR;  
}  
STDMETHODIMP CAutoClickDoc::XDualAClick::get_text(BSTR* retval)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick) *// MFC automatically converts from Ansi CString to *// Unicode BSTR,
    if necessary...  
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
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
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
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDisp;  
    lpDisp = pThis->GetPosition();
lpDisp->QueryInterface(IID_IDualAutoClickPoint, (LPVOID*)retval);

    return NOERROR;  
}  
```  
  
## <a name="registering-the-applications-type-library"></a>Inscription du type de bibliothèque de l'application  
 AppWizard ne génère pas de code pour enregistrer la bibliothèque de types d'une application serveur OLE Automation par le système. Lorsqu'il existe d'autres façons d'inscrire la bibliothèque de types, il est plus commode de faire en sorte que le registre de l'application enregistre la bibliothèque de types lorsqu'il met à jour ses informations de type OLE, c'est-à-dire chaque fois que l'application autonome est exécutée.  
  
 Pour inscrire la bibliothèque de types d'application chaque fois que l'application autonome est exécutée :  
  
-   Ajoutez AFXCTL.H à votre fichier d'en-tête includes standard, STDAFX.H, pour accéder à la définition de la fonction `AfxOleRegisterTypeLib`.  
  
-   Dans la fonction `InitInstance` de votre application, recherchez l'appel à `COleObjectFactory::UpdateRegistryAll`. Après cet appel, ajoutez un appel à `AfxOleRegisterTypeLib`, en spécifiant le **LIBID** correspondant à votre bibliothèque de types, ainsi que le nom de votre bibliothèque de types :  
  
 ''' * / / Quand une application serveur est lancée de façon autonome, il est judicieux * / / mettre à jour le Registre système, au cas où il a été endommagé.  
    m_server.UpdateRegistry(OAT_DISPATCH_OBJECT);

 COleObjectFactory::UpdateRegistryAll() ; * / / DUAL_SUPPORT_START * / / Assurez-vous que la bibliothèque de types est inscrite ou d’interface double ne fonctionne pas.  
AfxOleRegisterTypeLib(AfxGetInstanceHandle(), LIBID_ACDual, _T("AutoClik.TLB")) ; * / / DUAL_SUPPORT_END  
 ```  
  
## Modifying Project Build Settings to Accommodate Type Library Changes  
 To modify a project's build settings so that a header file containing **UUID** definitions is generated by MkTypLib whenever the type library is rebuilt:  
  
1.  On the **Build** menu, click **Settings**, and then select the ODL file from the file list for each configuration.  
  
2.  Click the **OLE Types** tab and specify a filename in the **Output header** filename field. Use a filename that is not already used by your project, because MkTypLib will overwrite any existing file. Click **OK** to close the **Build Settings** dialog box.  
  
 To add the **UUID** definitions from the MkTypLib-generated header file to your project:  
  
1.  Include the MkTypLib-generated header file in your standard includes header file, STDAFX.H.  
  
2.  Create a new file, INITIIDS.CPP, and add it to your project. In this file, include your MkTypLib-generated header file after including OLE2.H and INITGUID.H:  
  
 ```  
    initIIDs.c : définit les IID pour les interfaces doubles  
    Cela ne doit pas être généré avec l’en-tête précompilé.  
      #<a name="include-ole2h"></a>inclure < ole2.h >  
      #<a name="include-initguidh"></a>Incluez < initguid.h >  
      #<a name="include-acdualh"></a>inclure « acdual.h »  
 ```  
  
3.  On the **Build** menu, click **Settings**, and then select INITIIDS.CPP from the file list for each configuration.  
  
4.  Click the **C++** tab, click category **Precompiled Headers**, and select the **Not using precompiled headers** radio button. Click OK to close the **Build Settings** dialog box.  
  
## Specifying the Correct Object Class Name in the Type Library  
 The wizards shipped with Visual C++ incorrectly use the implementation class name to specify the coclass in the server's ODL file for OLE-creatable classes. While this will work, the implementation class name is probably not the class name you want users of your object to use. To specify the correct name, open the ODL file, locate each coclass statement, and replace the implementation class name with the correct external name.  
  
 Note that when the coclass statement is changed, the variable names of **CLSID**s in the MkTypLib-generated header file will change accordingly. You will need to update your code to use the new variable names.  
  
## Handling Exceptions and the Automation Error Interfaces  
 Your automation object's methods and property accessor functions may throw exceptions. If so, you should handle them in your dual-interface implementation and pass information about the exception back to the controller through the OLE Automation error-handling interface, `IErrorInfo`. This interface provides for detailed, contextual error information through both `IDispatch` and VTBL interfaces. To indicate that an error handler is available, you should implement the `ISupportErrorInfo` interface.  
  
 To illustrate the error-handling mechanism, assume that the ClassWizard-generated functions used to implement the standard dispatch support throw exceptions. MFC's implementation of `IDispatch::Invoke` typically catches these exceptions and converts them into an EXCEPTINFO structure that is returned through the `Invoke` call. However, when VTBL interface is used, you are responsible for catching the exceptions yourself. As an example of protecting your dual-interface methods:  
  
```  
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)  
{  
    METHOD_PROLOGUE (CAutoClickDoc, DualAClick)  
    TRY_DUAL(IID_IDualAClick) {* / / MFC convertit automatiquement des BSTR Unicode à * / / Ansi CString, si nécessaire...  
    pThis -> m_str = newText ;  
    Retourne NOERROR ;  
 }  
    CATCH_ALL_DUAL}  
```  
  
 `CATCH_ALL_DUAL` takes care of returning the correct error code when an exception occurs. `CATCH_ALL_DUAL` converts an MFC exception into OLE Automation error-handling information using the `ICreateErrorInfo` interface. (An example `CATCH_ALL_DUAL` macro is in the file MFCDUAL.H in the [ACDUAL](../visual-cpp-samples.md) sample. The function it calls to handle exceptions, `DualHandleException`, is in the file MFCDUAL.CPP.) `CATCH_ALL_DUAL` determines the error code to return based on the type of exception that occurred:  
  
- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) - In this case, `HRESULT` is constructed using the following code:  
  
 ```  
    hr = MAKE_HRESULT(SEVERITY_ERROR,
    FACILITY_ITF,   
 (e -> m_wCode + 0 x 200)) ;

 ```  
  
     This creates an `HRESULT` specific to the interface that caused the exception. The error code is offset by 0x200 to avoid any conflicts with system-defined `HRESULT`s for standard OLE interfaces.  
  
- [CMemoryException](../mfc/reference/cmemoryexception-class.md) - In this case, `E_OUTOFMEMORY` is returned.  
  
-   Any other exception - In this case, `E_UNEXPECTED` is returned.  
  
 To indicate that the OLE Automation error handler is used, you should also implement the `ISupportErrorInfo` interface.  
  
 First, add code to your automation class definition to show it supports `ISupportErrorInfo`.  
  
 Second, add code to your automation class's interface map to associate the `ISupportErrorInfo` implementation class with MFC's `QueryInterface` mechanism. The `INTERFACE_PART` statement matches the class defined for `ISupportErrorInfo`.  
  
 Finally, implement the class defined to support `ISupportErrorInfo`.  
  
 (The [ACDUAL](../visual-cpp-samples.md) sample contains three macros to help do these three steps, `DECLARE_DUAL_ERRORINFO`, `DUAL_ERRORINFO_PART`, and `IMPLEMENT_DUAL_ERRORINFO`, all contained in MFCDUAL.H.)  
  
 The following example implements a class defined to support `ISupportErrorInfo`. `CAutoClickDoc` is the name of your automation class and `IID_IDualAClick` is the **IID** for the interface that is the source of errors reported through the OLE Automation error object:  
  
```  
STDMETHODIMP_(ulong) CAutoClickDoc::XSupportErrorInfo::AddRef()   
{  
    METHOD_PROLOGUE (CAutoClickDoc, SupportErrorInfo)   
    retournés pThis -> ExternalAddRef() ;

}   
STDMETHODIMP_(ulong) CAutoClickDoc::XSupportErrorInfo::Release()   
{   
    METHOD_PROLOGUE (CAutoClickDoc, SupportErrorInfo)   
    retournés pThis -> ExternalRelease() ;

}   
STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::QueryInterface (REFIID iid, LPVOID * ppvObj)   
{   
    METHOD_PROLOGUE (CAutoClickDoc, SupportErrorInfo)   
    retournés pThis -> ExternalQueryInterface (& iid, ppvObj) ;

}   
STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::InterfaceSupportsErrorInfo (iid REFIID)   
{   
    METHOD_PROLOGUE (CAutoClickDoc, SupportErrorInfo)   
    retourner (iid == IID_IDualAClick) S_OK : S_FALSE ;   
}  
```  
  
## See Also  
 [Technical Notes by Number](../mfc/technical-notes-by-number.md)   
 [Technical Notes by Category](../mfc/technical-notes-by-category.md)

