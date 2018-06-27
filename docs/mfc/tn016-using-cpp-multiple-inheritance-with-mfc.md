---
title: 'TN016 : Utilisation de l’héritage Multiple C++ avec MFC | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.inheritance
dev_langs:
- C++
helpviewer_keywords:
- TN016
- MI (Multiple Inheritance)
- multiple inheritance, MFC support for
ms.assetid: 4ee27ae1-1410-43a5-b111-b6af9b84535d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cba37344a2d065c84e196330e3b4f9d859975102
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954856"
---
# <a name="tn016-using-c-multiple-inheritance-with-mfc"></a>TN016 : utilisation de l'héritage multiple C++ avec MFC
Cette note décrit l'utilisation de l'héritage multiple avec les classes Microsoft Foundation Class. L'utilisation de l'héritage multiple n'est pas nécessaire avec MFC. L'héritage multiple n'est pas utilisé dans les classes MFC et n'est pas nécessaire pour écrire une bibliothèque de classes.  
  
 Les sous-rubriques ci-dessous expliquent comment l'héritage multiple affecte l'utilisation des idiomes MFC courants et couvre certaines restrictions d'héritage multiple. Certaines de ces restrictions sont des restrictions C++ générales. D'autres sont imposées par l'architecture MFC.  
  
 À la fin de cette note technique, vous trouverez une application complète MFC qui utilise l'héritage multiple.  
  
## <a name="cruntimeclass"></a>CRuntimeClass  
 La persistance et les mécanismes de création d’objet dynamique de MFC utilisent le [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) structure de données pour identifier les classes. MFC associe une de ces structures à chaque classe dynamique et/ou sérialisable dans votre application. Ces structures sont initiées au démarrage de l'application à l'aide d'un objet statique spécial de type `AFX_CLASSINIT`.  
  
 L'implémentation actuelle de `CRuntimeClass` ne prend pas en charge les informations de type héritage multiple lors de l'exécution. Cela ne signifie pas que vous ne pouvez pas utiliser l'héritage multiple dans votre application MFC. Toutefois, vous avez certaines responsabilités lorsque vous utilisez des objets qui ont plusieurs classes de base.  
  
 Le [CObject::IsKindOf](../mfc/reference/cobject-class.md#iskindof) méthode pas correctement détermine le type d’un objet s’il a plusieurs classes de base. Par conséquent, vous ne pouvez pas utiliser [CObject](../mfc/reference/cobject-class.md) en tant que classe de base virtuelle et tous les appels à `CObject` telles que les fonctions membres [CObject::Serialize](../mfc/reference/cobject-class.md#serialize) et [denouveauCObject::operator](../mfc/reference/cobject-class.md#operator_new)doit avoir des qualificateurs de portée afin que C++ peut lever l’ambiguïté de l’appel de fonction appropriée. Lorsqu'un programme utilise l'héritage multiple dans MFC, la classe qui contient la classe de base `CObject` doit être la classe de gauche dans la liste des classes de base.  
  
 Une alternative consiste à utiliser l'opérateur `dynamic_cast`. Le cast d'un objet avec l'héritage multiple en une de ses classes de base force le compilateur à utiliser les fonctions de la classe de base fournie. Pour plus d’informations, consultez [opérateur dynamic_cast](../cpp/dynamic-cast-operator.md).  
  
## <a name="cobject---the-root-of-all-classes"></a>CObject - Racine de toutes les classes  
 Toutes les classes importantes sont dérivées directement ou indirectement de la classe `CObject`. `CObject` n'a pas de données membres, mais a certaines fonctionnalités par défaut. Lorsque vous utilisez l'héritage multiple, vous héritez généralement d'au-moins deux classes dérivées de `CObject`. L’exemple suivant illustre comment une classe peut hériter d’un [CFrameWnd](../mfc/reference/cframewnd-class.md) et un [CObList](../mfc/reference/coblist-class.md):  
  
```  
class CListWnd : public CFrameWnd, public CObList  
{  
 ...  
};  
CListWnd myListWnd;  
```  
  
 Dans ce cas, `CObject` est inclus deux fois. Cela signifie que vous avez besoin d'une méthode pour lever l'ambiguïté dans toute référence à des méthodes ou des opérateurs `CObject`. Le **new, opérateur** et [opérateur delete](../mfc/reference/cobject-class.md#operator_delete) sont deux opérateurs qui doivent être de lever l’ambiguïté. Autre exemple, le code suivant génère une erreur de compilation :  
  
```  
myListWnd.Dump(afxDump);
*// compile time error, CFrameWnd::Dump or CObList::Dump   
```  
  
## <a name="reimplementing-cobject-methods"></a>Réimplémentation des méthodes CObject  
 Lorsque vous créez une classe qui contient au moins deux classes de base dérivées de `CObject`, vous devez réimplémenter les méthodes `CObject` que vous voulez que d'autres personnes utilisent. Opérateurs **nouveau** et **supprimer** sont obligatoires et [Dump](../mfc/reference/cobject-class.md#dump) est recommandé. L’exemple suivant réimplémente les **nouveau** et **supprimer** opérateurs et le `Dump` méthode :  
  
```  
class CListWnd : public CFrameWnd, public CObList  
{  
public:  
    void* operator new(size_t nSize)  
 { return CFrameWnd:: operator new(nSize);

}  
    void operator delete(void* p)  
 { CFrameWnd:: operator delete(p);

}  
 
    void Dump(CDumpContent& dc)  
 { CFrameWnd::Dump(dc);

    CObList::Dump(dc);

} 
 ...  
};  
```  
  
## <a name="virtual-inheritance-of-cobject"></a>Héritage virtuel de CObject  
 Il peut sembler qu'hériter virtuellement `CObject` résoudrait le problème de l'ambiguïté de fonction, mais ce n'est pas le cas. Étant donné qu'il n'y a pas de données membres dans `CObject`, vous n'avez pas besoin de l'héritage virtuel pour éviter plusieurs copies des données membres d'une classe de base. Dans le premier exemple qui a été indiqué précédemment, la méthode virtuelle `Dump` est toujours ambiguë parce qu'elle est implémentée différemment dans `CFrameWnd` et `CObList`. La meilleure méthode pour éclaircir l'ambiguïté consiste à suivre les règles présentées dans la section précédente.  
  
## <a name="cobjectiskindof-and-run-time-typing"></a>CObject::IsKindOf et saisie à l'exécution  
 Le mécanisme de saisie exécution pris en charge par MFC dans `CObject` utilise les macros DECLARE_DYNAMIC, IMPLEMENT_DYNAMIC, DECLARE_DYNCREATE, IMPLEMENT_DYNCREATE, DECLARE_SERIAL et IMPLEMENT_SERIAL. Ces macros peuvent effectuer une vérification de type d'exécution pour vous assurer que les conversions en aval sont sécurisées.  
  
 Les macros prennent en charge une seule classe de base et s'exécutent de façon limitée pour multiplier les classes héritées. La classe de base que vous spécifiez dans IMPLEMENT_DYNAMIC ou IMPLEMENT_SERIAL doit être la classe de base premier (ou la plus à gauche). Ce positionnement vous permet de faire une vérification de type de la classe de base à gauche uniquement. Le système de types d'exécution ne sait rien des classes de base supplémentaires. Dans l'exemple suivant, les systèmes d'exécution font la vérification de type sur `CFrameWnd`, mais ne savent rien de `CObList`.  
  
```  
class CListWnd : public CFrameWnd,
    public CObList  
{  
    DECLARE_DYNAMIC(CListWnd) 
 ...  
};  
IMPLEMENT_DYNAMIC(CListWnd,
    CFrameWnd)  
```  
  
## <a name="cwnd-and-message-maps"></a>CWnd et tables de messages  
 Pour que le système de table de messages MFC fonctionne correctement, il existe deux autres conditions requises :  
  
-   Il doit n'y avoir qu'une classe de base dérivée de `CWnd`.  
  
-   La classe de base dérivée de `CWnd` doit être la première classe de base (ou la plus à gauche).  
  
 Voici quelques exemples qui ne fonctionnent pas :  
  
```  
class CTwoWindows : public CFrameWnd,
    public CEdit  
 { ... }; *// error : two copies of CWnd  
 
class CListEdit : public CObList,
    public CEdit  
 { ... }; *// error : CEdit (derived from CWnd) must be first  
```  
  
## <a name="a-sample-program-using-mi"></a>Un exemple de programme utilisant l'héritage multiple  
 L’exemple suivant est une application autonome qui se compose d’une classe dérivée de `CFrameWnd` et [CWinApp](../mfc/reference/cwinapp-class.md). Nous vous déconseillons de structurer une application de cette manière, mais il s'agit d'un exemple de la plus petite application MFC qui comporte une classe.  
  
```  
#include <afxwin.h>  
  
class CHelloAppAndFrame : public CFrameWnd, public CWinApp  
{   
public:  
    CHelloAppAndFrame()  
        { }  
  
    // Necessary because of MI disambiguity  
    void* operator new(size_t nSize)  
        { return CFrameWnd::operator new(nSize); }  
    void operator delete(void* p)  
        { CFrameWnd::operator delete(p); }  
  
    // Implementation  
    // CWinApp overrides  
    virtual BOOL InitInstance();  
    // CFrameWnd overrides  
    virtual void PostNcDestroy();  
    afx_msg void OnPaint();  
  
    DECLARE_MESSAGE_MAP()  
  
};  
  
BEGIN_MESSAGE_MAP(CHelloAppAndFrame, CFrameWnd)  
    ON_WM_PAINT()  
END_MESSAGE_MAP()  
  
// because the frame window is not allocated on the heap, we must  
// override PostNCDestroy not to delete the frame object  
void CHelloAppAndFrame::PostNcDestroy()  
{  
    // do nothing (do not call base class)  
}  
  
void CHelloAppAndFrame::OnPaint()  
{  
    CPaintDC dc(this);  
    CRect rect;  
    GetClientRect(rect);  
  
    CString s = "Hello, Windows!";  
    dc.SetTextAlign(TA_BASELINE | TA_CENTER);  
    dc.SetTextColor(::GetSysColor(COLOR_WINDOWTEXT));  
    dc.SetBkMode(TRANSPARENT);  
    dc.TextOut(rect.right / 2, rect.bottom / 2, s);  
}  
  
// Application initialization  
BOOL CHelloAppAndFrame::InitInstance()  
{  
    // first create the main frame  
    if (!CFrameWnd::Create(NULL, "Multiple Inheritance Sample",  
        WS_OVERLAPPEDWINDOW, rectDefault))  
        return FALSE;  
  
    // the application object is also a frame window  
    m_pMainWnd = this;            
    ShowWindow(m_nCmdShow);  
    return TRUE;  
}  
  
CHelloAppAndFrame theHelloAppAndFrame;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Notes techniques par numéro](../mfc/technical-notes-by-number.md)   
 [Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

