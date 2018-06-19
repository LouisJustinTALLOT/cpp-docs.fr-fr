---
title: Implémenter une Architecture de plug-in (C + c++ / CLI) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- plug-ins [C++]
- reflection [C++}, plug-ins
ms.assetid: 4f31e42b-78d1-48b9-8fdc-f28c75e8e77e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4e001ef88af0727a994c309d45167787d3e6677b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33135211"
---
# <a name="how-to-implement-a-plug-in-component-architecture-using-reflection-ccli"></a>Comment : implémenter une architecture de composants plug-in à l'aide de la réflexion (C++/CLI)
Les exemples de code suivants illustrent l’utilisation de la réflexion pour implémenter une architecture de « plug-in » simple. La première liste correspond à l’application, et le deuxième est le plug-in. L’application est un formulaire qui se remplit automatiquement à l’aide des classes basée sur formulaire trouvés dans la DLL de plug-in fournie comme argument de ligne de commande.  
  
 L’application tente de charger l’assembly fourni à l’aide de la <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> (méthode). Réussite, les types dans l’assembly sont énumérés à l’aide de la <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName> (méthode). Ensuite, chaque type est vérifiée pour la compatibilité à l’aide du <xref:System.Type.IsAssignableFrom%2A?displayProperty=fullName> (méthode). Dans cet exemple, les classes trouvés dans l’assembly fourni doivent être dérivées de la <xref:System.Windows.Forms.Form> classe pour être considérée comme un plug-in.  
  
 Les classes compatibles sont alors instanciées avec la <xref:System.Activator.CreateInstance%2A?displayProperty=fullName> (méthode), qui accepte un <xref:System.Type> en tant qu’argument et retourne un pointeur vers une nouvelle instance. Chaque nouvelle instance est ensuite jointe au formulaire et affiché.  
  
 Notez que le <xref:System.Reflection.Assembly.Load%2A> méthode n’accepte pas les noms d’assemblys qui incluent l’extension de fichier. La fonction principale de l’application tronque toute extension fournie, afin que l’exemple de code suivant fonctionne dans les deux cas.  
  
## <a name="example"></a>Exemple  
 Le code suivant définit l’application qui accepte des plug-ins. Un nom d’assembly doit être fourni comme premier argument. Cet assembly doit contenir au moins un public <xref:System.Windows.Forms.Form> type dérivé.  
  
```  
// plugin_application.cpp  
// compile with: /clr /c  
#using <system.dll>  
#using <system.drawing.dll>  
#using <system.windows.forms.dll>  
  
using namespace System;  
using namespace System::Windows::Forms;  
using namespace System::Reflection;  
  
ref class PluggableForm : public Form  {  
public:  
   PluggableForm() {}  
   PluggableForm(Assembly^ plugAssembly) {  
      Text = "plug-in example";  
      Size = Drawing::Size(400, 400);  
      IsMdiContainer = true;  
  
      array<Type^>^ types = plugAssembly->GetTypes( );  
      Type^ formType = Form::typeid;  
  
      for (int i = 0 ; i < types->Length ; i++) {  
         if (formType->IsAssignableFrom(types[i])) {  
            // Create an instance given the type description.  
            Form^ f = dynamic_cast<Form^> (Activator::CreateInstance(types[i]));  
            if (f) {  
               f->Text = types[i]->ToString();  
               f->MdiParent = this;  
               f->Show();  
            }  
         }  
      }  
   }  
};  
  
int main() {  
   Assembly^ a = Assembly::LoadFrom("plugin_application.exe");  
   Application::Run(gcnew PluggableForm(a));  
}  
```  
  
## <a name="example"></a>Exemple  
 Le code suivant définit trois classes dérivées de <xref:System.Windows.Forms.Form>. Quand le nom de l’assembly résultant est passé à l’exécutable dans la liste précédente, chacune de ces trois classes est découverts et instanciée, en dépit du fait qu’elles étaient toutes inconnues de l’application hôte au moment de la compilation.  
  
```  
// plugin_assembly.cpp  
// compile with: /clr /LD  
#using <system.dll>  
#using <system.drawing.dll>  
#using <system.windows.forms.dll>  
  
using namespace System;  
using namespace System::Windows::Forms;  
using namespace System::Reflection;  
using namespace System::Drawing;  
  
public ref class BlueForm : public Form {  
public:  
   BlueForm() {  
      BackColor = Color::Blue;  
   }  
};  
  
public ref class CircleForm : public Form {  
protected:  
   virtual void OnPaint(PaintEventArgs^ args) override {  
      args->Graphics->FillEllipse(Brushes::Green, ClientRectangle);  
   }  
};  
  
public ref class StarburstForm : public Form {  
public:  
   StarburstForm(){  
      BackColor = Color::Black;  
   }  
protected:  
   virtual void OnPaint(PaintEventArgs^ args) override {  
      Pen^ p = gcnew Pen(Color::Red, 2);  
      Random^ r = gcnew Random( );  
      Int32 w = ClientSize.Width;  
      Int32 h = ClientSize.Height;  
      for (int i=0; i<100; i++) {  
         float x1 = w / 2;  
         float y1 = h / 2;  
         float x2 = r->Next(w);  
         float y2 = r->Next(h);  
         args->Graphics->DrawLine(p, x1, y1, x2, y2);  
      }  
   }  
};  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Réflexion (C++-CLI)](../dotnet/reflection-cpp-cli.md)