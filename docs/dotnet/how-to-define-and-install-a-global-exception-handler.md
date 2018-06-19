---
title: 'Comment : définir et installer un gestionnaire d’exceptions Global | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- handlers, global
ms.assetid: dd88a812-3bc7-4ce8-8283-4b674c246534
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b77e982e3668ca23ece2eeeb5c609d71b30dc908
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33129682"
---
# <a name="how-to-define-and-install-a-global-exception-handler"></a>Comment : définir et installer un gestionnaire d'exceptions global
L’exemple de code suivant montre comment non prise en charge des exceptions peuvent être capturés. L’exemple de formulaire contient un bouton qui, lorsque vous appuyez sur, effectue une référence null, à l’origine d’une exception levée. Cette fonctionnalité représente un échec de code classique. L’exception qui en résulte est interceptée par le Gestionnaire d’exceptions de l’application installé par la fonction principale.  
  
 Cela est accompli en liant un délégué à le <xref:System.Windows.Forms.Application.ThreadException> événement. Dans ce cas, les exceptions suivantes sont ensuite envoyées à la `App::OnUnhandled` (méthode).  
  
## <a name="example"></a>Exemple  
  
```  
// global_exception_handler.cpp  
// compile with: /clr  
#using <system.dll>  
#using <system.drawing.dll>  
#using <system.windows.forms.dll>  
  
using namespace System;  
using namespace System::Threading;  
using namespace System::Drawing;  
using namespace System::Windows::Forms;  
  
ref class MyForm : public Form  
{  
   Button^ b;  
public:  
   MyForm( )  
   {  
      b = gcnew Button( );  
      b->Text = "Do Null Access";  
      b->Size = Drawing::Size(150, 30);  
      b->Click += gcnew EventHandler(this, &MyForm::OnClick);  
      Controls->Add(b);  
   }  
   void OnClick(Object^ sender, EventArgs^ args)   
   {  
      // do something illegal, like call through a null pointer...  
      Object^ o = nullptr;  
      o->ToString( );        
   }  
};  
  
ref class App  
{  
public:  
   static void OnUnhandled(Object^ sender, ThreadExceptionEventArgs^ e)  
   {  
      MessageBox::Show(e->Exception->Message, "Global Exeception");  
      Application::ExitThread( );  
   }  
};  
  
int main()  
{  
   Application::ThreadException += gcnew   
      ThreadExceptionEventHandler(App::OnUnhandled);  
  
   MyForm^ form = gcnew MyForm( );  
   Application::Run(form);  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des exceptions](../windows/exception-handling-cpp-component-extensions.md)