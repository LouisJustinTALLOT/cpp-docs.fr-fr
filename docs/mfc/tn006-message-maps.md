---
title: 'TN006 : Tables des messages | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.messages.maps
dev_langs:
- C++
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- ON_NOTIFY_RANGE macro [MFC]
- ON_COMMAND macro [MFC]
- ON_CONTROL_RANGE macro [MFC]
- ON_REGISTERED_MESSAGE macro [MFC]
- ON_NOTIFY message [MFC]
- ON_COMMAND_RANGE_EX macro [MFC]
- ON_MESSAGE macro [MFC]
- Windows messages [MFC], message maps
- ON_COMMAND_RANGE macro [MFC]
- TN006
- ON_CONTROL macro [MFC]
- ON_COMMAND_EX macro [MFC]
- message maps [MFC], Windows messaging
ms.assetid: af4b6794-4b40-4f1e-ad41-603c3b7409bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 160b88a7069ac9a5851c0f472f756d694e59874e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384695"
---
# <a name="tn006-message-maps"></a>TN006 : tables des messages
Cette note décrit la fonctionnalité de mappage de messages MFC.  
  
## <a name="the-problem"></a>Le problème  
 Microsoft Windows implémente des fonctions virtuelles dans les classes de fenêtre qui utilisent la fonction de messagerie. En raison du grand nombre de messages impliquée, en fournissant une fonction virtuelle distincte pour chaque message Windows créerait un vtable trop importante.  
  
 Étant donné que le nombre de messages de Windows définis par le système change au fil du temps, et les tables des messages, car les applications peuvent définir leurs propres messages Windows, fournir un niveau d’indirection qui empêche les modifications de l’interface à partir de la rupture du code existant.  
  
## <a name="overview"></a>Vue d'ensemble  
 MFC fournit une alternative à l’instruction switch qui a été utilisée dans des programmes Windows traditionnels pour traiter les messages envoyés à une fenêtre. Un mappage à partir des messages aux méthodes peut être défini lorsqu’un message est reçu par une fenêtre, la méthode appropriée est appelée automatiquement. Cette fonctionnalité de la table des messages est conçue pour ressembler à des fonctions virtuelles, mais présente des avantages supplémentaires n’est pas possibles avec les fonctions virtuelles C++.  
  
## <a name="defining-a-message-map"></a>Définition d’une table des messages  
 Le [DECLARE_MESSAGE_MAP](reference/message-map-macros-mfc.md#declare_message_map) macro déclare trois membres d’une classe.  
  
-   Un tableau privé de `AFX_MSGMAP_ENTRY` entrées appelées `_messageEntries`.  
  
-   Un document protégé `AFX_MSGMAP` structure appelée `messageMap` qui pointe vers le `_messageEntries` tableau.  
  
-   A protégé par la fonction virtuelle appelée `GetMessageMap` qui retourne l’adresse de `messageMap`.  
  
 Cette macro doit être placée dans la déclaration d’une classe à l’aide des tables des messages. Par convention, il est à la fin de la déclaration de classe. Par exemple :  
  
```  
class CMyWnd : public CMyParentWndClass  
{ *// my stuff...  
 
protected: *//{{AFX_MSG(CMyWnd)  
    afx_msg void OnPaint();
*//}}AFX_MSG  
 
    DECLARE_MESSAGE_MAP() 
};  
```  
  
 Il s’agit du format généré par AppWizard et ClassWizard lorsqu’ils créent de nouvelles classes. La / / {{et / /}} crochets sont nécessaires pour ClassWizard.  
  
 Tableau de la table des messages est définie à l’aide d’un ensemble de macros qui s’étendent aux entrées de mappage de message. Un tableau commence par un [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) appel de macro qui définit la classe qui est gérée par ce mappage de message et la classe parente à laquelle les messages non prise en charge sont passés. Le tableau se termine par le [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map) appel de macro.  
  
 Entre les appels de ces deux macros est une entrée pour chaque message d’être géré par ce mappage de message. Tous les messages Windows standard a une macro sous la forme ON_WM_*MESSAGE_NAME* qui génère une entrée pour ce message.  
  
 Une signature de fonction standard a été définie pour décompresser les paramètres de chaque message Windows et de fournir la sécurité de type. Ces signatures peuvent être trouvées dans le fichier Afxwin.h dans la déclaration de [CWnd](../mfc/reference/cwnd-class.md). Chacun d’eux est marqué avec le mot clé `afx_msg` pour faciliter l’identification.  
  
> [!NOTE]
>  ClassWizard exige que vous utilisiez le `afx_msg` mot clé dans les déclarations de gestionnaire de mappage de message.  
  
 Ces signatures de fonction ont été dérivées à l’aide d’une convention simple. Le nom de la fonction commence toujours par `"On`». Il est suivi par le nom du message Windows avec « WM_ » supprimé et la première lettre de chaque mot en majuscules. L’ordre des paramètres est `wParam` suivie `LOWORD`(`lParam`) puis `HIWORD`(`lParam`). Les paramètres inutilisés ne sont pas transmis. Tous les handles qui sont encapsulés par les classes MFC sont convertis en pointeurs vers les objets MFC appropriés. L’exemple suivant montre comment gérer les `WM_PAINT` le message et provoquer la `CMyWnd::OnPaint` fonction à appeler :  
  
```  
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass) *//{{AFX_MSG_MAP(CMyWnd)  
    ON_WM_PAINT() *//}}AFX_MSG_MAP  
END_MESSAGE_MAP()  
```  
  
 Le tableau de mappage de message doit être défini en dehors de toute définition de fonction ou une classe. Il ne doit pas être placé dans un bloc d’extern « C ».  
  
> [!NOTE]
>  ClassWizard modifiera les entrées de mappage de message qui se produisent entre le / / {{et / /}} crochet de commentaire.  
  
## <a name="user-defined-windows-messages"></a>Messages Windows défini par l’utilisateur  
 Les messages définis par l’utilisateur peuvent être inclus dans une table des messages à l’aide de la [ON_MESSAGE](reference/message-map-macros-mfc.md#on_message) (macro). Cette macro accepte un numéro de message et une méthode sous la forme :  
  
''' * / / à l’intérieur de la déclaration de classe  
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam) ;

 
 #<a name="define-wmmymessage-wmuser--100"></a>définir WM_MYMESSAGE (WM_USER + 100)  
 
BEGIN_MESSAGE_MAP (CMyWnd, CMyParentWndClass)  
    ON_MESSAGE (WM_MYMESSAGE, OnMyMessage)  
END_MESSAGE_MAP()  
```  
  
 In this example, we establish a handler for a custom message that has a Windows message ID derived from the standard `WM_USER` base for user-defined messages. The following example shows how to call this handler:  
  
```  
CWnd * pWnd =... ;  
pWnd -> SendMessage(WM_MYMESSAGE) ;
```  
  
 The range of user-defined messages that use this approach must be in the range `WM_USER` to 0x7fff.  
  
> [!NOTE]
>  ClassWizard does not support entering `ON_MESSAGE` handler routines from the ClassWizard user interface. You must manually enter them from the Visual C++ editor. ClassWizard will parse these entries and let you browse them just like any other message-map entries.  
  
## Registered Windows Messages  
 The [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947) function is used to define a new window message that is guaranteed to be unique throughout the system. The macro `ON_REGISTERED_MESSAGE` is used to handle these messages. This macro accepts a name of a `UINT NEAR` variable that contains the registered windows message ID. For example  
  
```  
classe CMyWnd : CMyParentWndClass public  
{  
publique :  
    CMyWnd() ;

 *//{{AFX_MSG(CMyWnd)  
    afx_msg LRESULT OnFind(WPARAM wParam, LPARAM lParam) ; * //}}AFX_MSG  
 
    DECLARE_MESSAGE_MAP() 
};  
 
UINT statique près WM_FIND = RegisterWindowMessage("COMMDLG_FIND") ;

 
BEGIN_MESSAGE_MAP (CMyWnd, CMyParentWndClass) *//{{AFX_MSG_MAP(CMyWnd)  
    ON_REGISTERED_MESSAGE (WM_FIND, OnFind) * //}}AFX_MSG_MAP  
END_MESSAGE_MAP()  
```  
  
 The registered Windows message ID variable (WM_FIND in this example) must be a `NEAR` variable because of the way `ON_REGISTERED_MESSAGE` is implemented.  
  
 The range of user-defined messages that use this approach will be in the range 0xC000 to 0xFFFF.  
  
> [!NOTE]
>  ClassWizard does not support entering `ON_REGISTERED_MESSAGE` handler routines from the ClassWizard user interface. You must manually enter them from the text editor. ClassWizard will parse these entries and let you browse them just like any other message-map entries.  
  
## Command Messages  
 Command messages from menus and accelerators are handled in message maps with the `ON_COMMAND` macro. This macro accepts a command ID and a method. Only the specific `WM_COMMAND` message that has a `wParam` equal to the specified command ID is handled by the method specified in the message-map entry. Command handler member functions take no parameters and return `void`. The macro has the following form:  
  
```  
ON_COMMAND (id, memberFxn)  
```  
  
 Command update messages are routed through the same mechanism, but use the `ON_UPDATE_COMMAND_UI` macro instead. Command update handler member functions take a single parameter, a pointer to a [CCmdUI](../mfc/reference/ccmdui-class.md) object, and return `void`. The macro has the form  
  
```  
ON_UPDATE_COMMAND_UI (id, memberFxn)  
```  
  
 Advanced users can use the `ON_COMMAND_EX` macro, which is an extended form of command message handlers. The macro provides a superset of the `ON_COMMAND` functionality. Extended command-handler member functions take a single parameter, a `UINT` that contains the command ID, and return a `BOOL`. The return value should be `TRUE` to indicate that the command has been handled. Otherwise routing will continue to other command target objects.  
  
 Examples of these forms:  
  
-   Inside Resource.h (usually generated by Visual C++)  
  
 ```  
 #<a name="define----idmycmd------100"></a>définir ID_MYCMD 100  
 #<a name="define----idcomplex----101"></a>définir ID_COMPLEX 101  
 ```  
  
-   Inside the class declaration  
  
 ```  
    afx_msg void OnMyCommand();
afx_msg void OnUpdateMyCommand (CCmdUI * pCmdUI) ;

    afx_msg BOOL OnComplexCommand(UINT nID);

 ```  
  
-   Inside the message map definition  
  
 ```  
    ON_COMMAND(ID_MYCMD,
    OnMyCommand)  
    ON_UPDATE_COMMAND_UI(ID_MYCMD,
    OnUpdateMyCommand)  
    ON_COMMAND_EX(ID_MYCMD,
    OnComplexCommand)  
 ```  
  
-   In the implementation file  
  
 ```  
    void CMyClass::OnMyCommand()  
 {* / / gérer la commande  
 }  
 
    void CMyClass::OnUpdateMyCommand(CCmdUI* pCmdUI)  
 {* / / définir l’état de l’interface utilisateur avec pCmdUI  
 }  
 
    BOOL CMyClass::OnComplexCommand(UINT nID)  
 {* / / gérer la commande  
    Renvoie la valeur TRUE ;  
 }  
 ```  
  
 Advanced users can handle a range of commands by using a single command handler: [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range) or `ON_COMMAND_RANGE_EX`. See the product documentation for more information about these macros.  
  
> [!NOTE]
>  ClassWizard supports creating `ON_COMMAND` and `ON_UPDATE_COMMAND_UI` handlers, but it does not support creating `ON_COMMAND_EX` or `ON_COMMAND_RANGE` handlers. However, Class Wizard will parse and let you browse all four command handler variants.  
  
## Control Notification Messages  
 Messages that are sent from child controls to a window have an extra bit of information in their message map entry: the control's ID. The message handler specified in a message map entry is called only if the following conditions are true:  
  
-   The control notification code (high word of `lParam`), such as BN_CLICKED, matches the notification code specified in the message-map entry.  
  
-   The control ID (`wParam`) matches the control ID specified in the message-map entry.  
  
 Custom control notification messages may use the [ON_CONTROL](reference/message-map-macros-mfc.md#on_control) macro to define a message map entry with a custom notification code. This macro has the form  
  
```  
ON_CONTROL (wNotificationCode, id, memberFxn)  
```  
  
 For advanced usage [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range) can be used to handle a specific control notification from a range of controls with the same handler.  
  
> [!NOTE]
>  ClassWizard does not support creating an `ON_CONTROL` or `ON_CONTROL_RANGE` handler in the user interface. You must manually enter them with the text editor. ClassWizard will parse these entries and let you browse them just like any other message map entries.  
  
 The Windows Common Controls use the more powerful [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583) for complex control notifications. This version of MFC has direct support for this new message by using the `ON_NOTIFY` and `ON_NOTIFY_RANGE` macros. See the product documentation for more information about these macros.  
  
## See Also  
 [Technical Notes by Number](../mfc/technical-notes-by-number.md)   
 [Technical Notes by Category](../mfc/technical-notes-by-category.md)

