---
title: "Comment : définir et installer un gestionnaire d'exceptions global"
ms.date: 11/04/2016
helpviewer_keywords:
- handlers, global
ms.assetid: dd88a812-3bc7-4ce8-8283-4b674c246534
ms.openlocfilehash: 9c6f355bc43fc53d2b8d27a1ee69c059d0f50692
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534535"
---
# <a name="how-to-define-and-install-a-global-exception-handler"></a>Comment : définir et installer un gestionnaire d'exceptions global

L’exemple de code suivant montre comment non prise en charge des exceptions peuvent être capturées. L’exemple de formulaire contienne un bouton qui, lorsque vous appuyez sur, effectue une référence null, à l’origine d’une exception levée. Cette fonctionnalité représente un échec de code typique. L’exception qui en résulte est interceptée par le Gestionnaire d’exceptions de l’application installé par la fonction principale.

Pour cela en liant un délégué à la <xref:System.Windows.Forms.Application.ThreadException> événement. Dans ce cas, les exceptions suivantes sont ensuite envoyées à la `App::OnUnhandled` (méthode).

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