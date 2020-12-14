---
description: 'En savoir plus sur : Comment : définir et installer un gestionnaire d’exceptions global'
title: "Comment : définir et installer un gestionnaire d'exceptions global"
ms.date: 11/04/2016
helpviewer_keywords:
- handlers, global
ms.assetid: dd88a812-3bc7-4ce8-8283-4b674c246534
ms.openlocfilehash: 6747e0bdf95ae4d87ed667576852c282e05a7d6d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258328"
---
# <a name="how-to-define-and-install-a-global-exception-handler"></a>Comment : définir et installer un gestionnaire d'exceptions global

L’exemple de code suivant montre comment les exceptions non gérées peuvent être capturées. L’exemple de formulaire contient un bouton qui, lorsqu’il est enfoncé, exécute une référence null, provoquant la levée d’une exception. Cette fonctionnalité représente un échec de code standard. L’exception résultante est interceptée par le gestionnaire d’exceptions au niveau de l’application installé par la fonction principale.

Pour ce faire, vous devez lier un délégué à l' <xref:System.Windows.Forms.Application.ThreadException> événement. Dans ce cas, les exceptions suivantes sont ensuite envoyées à la `App::OnUnhandled` méthode.

## <a name="example"></a>Exemple

```cpp
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

[Gestion des exceptions](../extensions/exception-handling-cpp-component-extensions.md)
