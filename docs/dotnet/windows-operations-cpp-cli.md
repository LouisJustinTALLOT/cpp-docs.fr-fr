---
title: Les opérations Windows (C++ / c++ / CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows [C++], Windows-specific tasks
- .NET Framework [C++], Windows operations
- Visual C++, Windows operations
- Windows operations [C++]
- .NET Framework, shutdown
- shutdown
- termination
- applications [C++], shutdown
- Visual C++, user interactive state
- user interactive state
- Visual C++, reading from Windows Registry
- registry, reading
- performance counters
- performance counters, reading Windows performance counters
- performance monitoring, Windows performance counters
- performance, counters
- counters, reading Windows performance counters
- performance
- performance monitoring
- text, retrieving from Clipboard
- Clipboard, retrieving text
- current user names
- user names, retrieving
- UserName string
- .NET Framework, version
- Version property, retrieving .NET Framework version
- computer name, retrieving
- machine name, retrieving
- computer name
- Windows [C++], version
- Windows [C++], retrieving version using Visual C++
- time, elapsed since startup
- counters, elapsed time
- startup, time elapsed since
- tick counts
- startup
- text, storing in Clipboard
- Clipboard, storing text
- registry, writing to
- Visual C++, writing to Windows Registry
ms.assetid: b9a75cb4-0589-4d5b-92cb-5e8be42b4ac0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 198fd5bee9ea65888f24a0514ed6a2b79b0fa8c3
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678027"
---
# <a name="windows-operations-ccli"></a>Opérations Windows (C++/CLI)
Illustre différentes tâches spécifiques à Windows en utilisant le SDK Windows.  
  
 Les rubriques suivantes montrent les différentes opérations Windows exécutées avec le Kit de développement Windows à l’aide de Visual C++.  

## <a name="determine_shutdown"></a> Déterminer si le processus d’arrêt a commencé
L’exemple de code suivant montre comment déterminer si l’application ou le .NET Framework s’arrête. Cela est utile pour accéder à des éléments statiques dans le .NET Framework, car, lors de l’arrêt, ces constructions sont finalisées par le système et ne peut pas être utilisées de façon fiable. En vérifiant la <xref:System.Environment.HasShutdownStarted%2A> propriété tout d’abord, vous pouvez éviter des défaillances potentielles en n’accède à ces éléments.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// check_shutdown.cpp  
// compile with: /clr  
using namespace System;  
int main()   
{  
   if (Environment::HasShutdownStarted)  
      Console::WriteLine("Shutting down.");  
   else  
      Console::WriteLine("Not shutting down.");  
   return 0;  
}  
```  

## <a name="determine_user"></a> Déterminer l’état interactif d’utilisateur
L’exemple de code suivant montre comment déterminer si le code est exécuté dans un contexte utilisateur interactif. Si <xref:System.Environment.UserInteractive%2A> est false, le code s’exécute comme un processus de service ou à partir d’à l’intérieur d’une application Web, auquel cas vous devez interagir avec l’utilisateur.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// user_interactive.cpp  
// compile with: /clr  
using namespace System;  
  
int main()   
{  
   if ( Environment::UserInteractive )  
      Console::WriteLine("User interactive");  
   else  
      Console::WriteLine("Noninteractive");  
   return 0;  
}  
```  

## <a name="read_registry"></a> Lire les données à partir du Registre Windows
Le code suivant exemple utilise le <xref:Microsoft.Win32.Registry.CurrentUser> clé pour lire les données à partir du Registre Windows. Tout d’abord, les sous-clés sont énumérées à l’aide de la <xref:Microsoft.Win32.RegistryKey.GetSubKeyNames%2A> (méthode), puis la sous-clé Identities est ouverte à l’aide du <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> (méthode). Comme les clés racine, chaque sous-clé est représentée par la <xref:Microsoft.Win32.RegistryKey> classe. Enfin, la nouvelle <xref:Microsoft.Win32.RegistryKey> objet est utilisé pour énumérer les paires clé/valeur.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// registry_read.cpp  
// compile with: /clr  
using namespace System;  
using namespace Microsoft::Win32;  
  
int main( )  
{  
   array<String^>^ key = Registry::CurrentUser->GetSubKeyNames( );  
  
   Console::WriteLine("Subkeys within CurrentUser root key:");  
   for (int i=0; i<key->Length; i++)  
   {  
      Console::WriteLine("   {0}", key[i]);  
   }  
  
   Console::WriteLine("Opening subkey 'Identities'...");  
   RegistryKey^ rk = nullptr;  
   rk = Registry::CurrentUser->OpenSubKey("Identities");  
   if (rk==nullptr)  
   {  
      Console::WriteLine("Registry key not found - aborting");  
      return -1;  
   }  
  
   Console::WriteLine("Key/value pairs within 'Identities' key:");  
   array<String^>^ name = rk->GetValueNames( );  
   for (int i=0; i<name->Length; i++)  
   {  
      String^ value = rk->GetValue(name[i])->ToString();  
      Console::WriteLine("   {0} = {1}", name[i], value);  
   }  
  
   return 0;  
}  
```  
  
### <a name="remarks"></a>Notes  
 Le <xref:Microsoft.Win32.Registry> classe est simplement un conteneur pour les instances statiques de <xref:Microsoft.Win32.RegistryKey>. Chaque instance représente un nœud de Registre racine. Les instances sont <xref:Microsoft.Win32.Registry.ClassesRoot>, <xref:Microsoft.Win32.Registry.CurrentConfig>, <xref:Microsoft.Win32.Registry.CurrentUser>, <xref:Microsoft.Win32.Registry.LocalMachine>, et <xref:Microsoft.Win32.Registry.Users>.  
  
 En plus d’être statiques, les objets au sein de la <xref:Microsoft.Win32.Registry> classe sont en lecture seule. En outre, les instances de la <xref:Microsoft.Win32.RegistryKey> sont en lecture seule ainsi des objets de classe sont créées pour accéder au contenu du Registre. Pour obtenir un exemple montrant comment substituer ce comportement, consultez [Comment : écrire les données dans le Registre Windows (C++ / c++ / CLI)](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md).  
  
 Il existe deux objets supplémentaires dans le <xref:Microsoft.Win32.Registry> classe : <xref:Microsoft.Win32.Registry.DynData> et <xref:Microsoft.Win32.Registry.PerformanceData>. Les deux sont des instances de la <xref:Microsoft.Win32.RegistryKey> classe. Le <xref:Microsoft.Win32.Registry.DynData> objet contient des informations de Registre dynamiques, qui sont uniquement pris en charge dans Windows 98 et Windows Me. Le <xref:Microsoft.Win32.Registry.PerformanceData> objet peut être utilisé pour accéder aux informations de compteur de performances pour les applications qui utilisent le système de surveillance des performances de Windows. Le <xref:Microsoft.Win32.Registry.PerformanceData> nœud représente des informations qui ne sont pas réellement stockées dans le Registre et par conséquent ne peut pas apparaître à l’aide de Regedit.exe.  

## <a name="read_performance"></a> Lire les compteurs de performances Windows
Certaines applications et les sous-systèmes de Windows exposent des données de performances via le système de performances Windows. Ces compteurs sont accessibles à l’aide de la <xref:System.Diagnostics.PerformanceCounterCategory> et <xref:System.Diagnostics.PerformanceCounter> classes, qui se trouvent dans le <xref:System.Diagnostics?displayProperty=fullName> espace de noms.  
  
 L’exemple de code suivant utilise ces classes pour récupérer et afficher un compteur qui est mis à jour par Windows pour indiquer le pourcentage de temps que le processeur est occupé.  
  
> [!NOTE]
>  L’exécution de cet exemple sur Windows Vista nécessite des privilèges d’administrateur.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// processor_timer.cpp  
// compile with: /clr  
#using <system.dll>  
  
using namespace System;  
using namespace System::Threading;  
using namespace System::Diagnostics;  
using namespace System::Timers;  
  
ref struct TimerObject  
{  
public:  
   static String^ m_instanceName;  
   static PerformanceCounter^ m_theCounter;  
  
public:  
   static void OnTimer(Object^ source, ElapsedEventArgs^ e)  
   {  
      try   
      {  
         Console::WriteLine("CPU time used: {0,6} ",  
          m_theCounter->NextValue( ).ToString("f"));  
      }   
      catch(Exception^ e)  
      {  
         if (dynamic_cast<InvalidOperationException^>(e))  
         {  
            Console::WriteLine("Instance '{0}' does not exist",  
                  m_instanceName);  
            return;  
         }  
         else  
         {  
            Console::WriteLine("Unknown exception... ('q' to quit)");  
            return;  
         }  
      }  
   }  
};  
  
int main()  
{  
   String^ objectName = "Processor";  
   String^ counterName = "% Processor Time";  
   String^ instanceName = "_Total";  
  
   try  
   {  
      if ( !PerformanceCounterCategory::Exists(objectName) )  
      {  
         Console::WriteLine("Object {0} does not exist", objectName);  
         return -1;  
      }  
   }  
   catch (UnauthorizedAccessException ^ex)  
   {  
      Console::WriteLine("You are not authorized to access this information.");  
      Console::Write("If you are using Windows Vista, run the application with ");  
      Console::WriteLine("administrative privileges.");  
      Console::WriteLine(ex->Message);  
      return -1;  
   }  
  
   if ( !PerformanceCounterCategory::CounterExists(  
          counterName, objectName) )  
   {  
      Console::WriteLine("Counter {0} does not exist", counterName);  
      return -1;  
   }  
  
   TimerObject::m_instanceName = instanceName;  
   TimerObject::m_theCounter = gcnew PerformanceCounter(  
          objectName, counterName, instanceName);  
  
   System::Timers::Timer^ aTimer = gcnew System::Timers::Timer();  
   aTimer->Elapsed += gcnew ElapsedEventHandler(&TimerObject::OnTimer);  
   aTimer->Interval = 1000;  
   aTimer->Enabled = true;  
   aTimer->AutoReset = true;  
  
   Console::WriteLine("reporting CPU usage for the next 10 seconds");  
   Thread::Sleep(10000);  
   return 0;  
}  
```  

## <a name="retrieve_text"></a> Récupérer du texte dans le Presse-papiers
Le code suivant exemple utilise le <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> fonction membre pour retourner un pointeur vers le <xref:System.Windows.Forms.IDataObject> interface. Cette interface peut ensuite être interrogée pour le format des données et permet de récupérer les données réelles.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// read_clipboard.cpp  
// compile with: /clr  
#using <system.dll>  
#using <system.Drawing.dll>  
#using <system.windows.forms.dll>  
  
using namespace System;  
using namespace System::Windows::Forms;  
  
[STAThread] int main( )  
{  
   IDataObject^ data = Clipboard::GetDataObject( );  
  
   if (data)  
   {  
      if (data->GetDataPresent(DataFormats::Text))   
      {  
         String^ text = static_cast<String^>  
           (data->GetData(DataFormats::Text));  
         Console::WriteLine(text);   
      }  
      else  
         Console::WriteLine("Nontext data is in the Clipboard.");  
   }  
   else   
   {  
      Console::WriteLine("No data was found in the Clipboard.");  
   }  
  
   return 0;  
}  
```  

## <a name="retrieve_current"></a> Récupérer le nom d’utilisateur actuel
L’exemple de code suivant illustre la récupération du nom d’utilisateur actuel (le nom de l’utilisateur connecté à Windows). Le nom est stocké dans le <xref:System.Environment.UserName%2A> chaîne, qui est défini dans le <xref:System.Environment> espace de noms.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// username.cpp  
// compile with: /clr  
using namespace System;  
  
int main()   
{  
   Console::WriteLine("\nCurrent user: {0}", Environment::UserName);  
   return 0;  
}  
```  

## <a name="retrieve_dotnet"></a> Récupérer la Version du .NET Framework
L’exemple de code suivant montre comment déterminer la version du .NET Framework actuellement installée avec le <xref:System.Environment.Version%2A> propriété, qui est un pointeur vers un <xref:System.Version> objet qui contient les informations de version.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// dotnet_ver.cpp  
// compile with: /clr  
using namespace System;  
int main()   
{  
   Version^ version = Environment::Version;  
   if (version)  
   {  
      int build = version->Build;  
      int major = version->Major;  
      int minor = version->Minor;  
      int revision = Environment::Version->Revision;  
      Console::Write(".NET Framework version: ");  
      Console::WriteLine("{0}.{1}.{2}.{3}",   
            build, major, minor, revision);  
   }  
   return 0;  
}  
```  

## <a name="retrieve_local"></a> Récupérer le nom de l’ordinateur Local 
L’exemple de code suivant illustre la récupération du nom de l’ordinateur local (le nom de l’ordinateur tel qu’il apparaît sur un réseau). Vous pouvez y parvenir en obtenant le <xref:System.Environment.MachineName%2A> chaîne, qui est défini dans le <xref:System.Environment> espace de noms.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// machine_name.cpp  
// compile with: /clr  
using namespace System;  
  
int main()   
{  
   Console::WriteLine("\nMachineName: {0}", Environment::MachineName);  
   return 0;  
}  
```  

## <a name="retrieve_version"></a> Récupérer la Version de Windows
L’exemple de code suivant montre comment récupérer les informations de plateforme et la version du système d’exploitation actuel. Ces informations sont stockées dans le <xref:System.Environment.OSVersion%2A?displayProperty=fullName> propriété et se compose d’une énumération qui décrit la version de Windows dans les grandes lignes et un <xref:System.Environment.Version%2A> objet qui contient la version exacte du système d’exploitation.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// os_ver.cpp  
// compile with: /clr  
using namespace System;  
  
int main()   
{  
   OperatingSystem^ osv = Environment::OSVersion;  
   PlatformID id = osv->Platform;  
   Console::Write("Operating system: ");  
  
   if (id == PlatformID::Win32NT)  
      Console::WriteLine("Win32NT");  
   else if (id == PlatformID::Win32S)  
      Console::WriteLine("Win32S");  
   else if (id == PlatformID::Win32Windows)  
      Console::WriteLine("Win32Windows");  
   else  
      Console::WriteLine("WinCE");  
  
   Version^ version = osv->Version;  
   if (version)  
   {  
      int build = version->Build;  
      int major = version->Major;  
      int minor = version->Minor;  
      int revision = Environment::Version->Revision;  
      Console::Write("OS Version: ");  
      Console::WriteLine("{0}.{1}.{2}.{3}",   
                   build, major, minor, revision);  
   }  
  
   return 0;  
}  
```  

## <a name="retrieve_time"></a> Récupérer le temps écoulé depuis le démarrage
L’exemple de code suivant montre comment déterminer le nombre de cycles, ou nombre de millisecondes qui se sont écoulées depuis Windows a été démarré. Cette valeur est stockée dans le <xref:System.Environment.TickCount%2A?displayProperty=fullName> membre et, s’agissant d’une valeur 32 bits, remet à zéro tous les 24,9 jours environ.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// startup_time.cpp  
// compile with: /clr  
using namespace System;  
  
int main( )   
{  
   Int32 tc = Environment::TickCount;  
   Int32 seconds = tc / 1000;  
   Int32 minutes = seconds / 60;  
   float hours = static_cast<float>(minutes) / 60;  
   float days = hours / 24;  
  
   Console::WriteLine("Milliseconds since startup: {0}", tc);  
   Console::WriteLine("Seconds since startup: {0}", seconds);  
   Console::WriteLine("Minutes since startup: {0}", minutes);  
   Console::WriteLine("Hours since startup: {0}", hours);  
   Console::WriteLine("Days since startup: {0}", days);  
  
   return 0;  
}  
```  

## <a name="store_text"></a> Texte de Store dans le Presse-papiers
Le code suivant exemple utilise le <xref:System.Windows.Forms.Clipboard> objet défini dans le <xref:System.Windows.Forms> espace de noms pour stocker une chaîne. Cet objet fournit deux fonctions membres : <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> et <xref:System.Windows.Forms.Clipboard.GetDataObject%2A>. Données sont stockées dans le Presse-papiers en envoyant tout objet dérivé <xref:System.Object> à <xref:System.Windows.Forms.Clipboard.SetDataObject%2A>.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// store_clipboard.cpp  
// compile with: /clr  
#using <System.dll>  
#using <System.Drawing.dll>  
#using <System.Windows.Forms.dll>  
  
using namespace System;  
using namespace System::Windows::Forms;  
  
[STAThread] int main()  
{  
   String^ str = "This text is copied into the Clipboard.";  
  
   // Use 'true' as the second argument if  
   // the data is to remain in the clipboard  
   // after the program terminates.  
   Clipboard::SetDataObject(str, true);  
  
   Console::WriteLine("Added text to the Clipboard.");  
  
   return 0;  
}  
```  

## <a name="write_data"></a> Écrire des données dans le Registre Windows
Le code suivant exemple utilise le <xref:Microsoft.Win32.Registry.CurrentUser> clé à créer une instance accessible en écriture de la <xref:Microsoft.Win32.RegistryKey> classe qui correspond à la **logiciel** clé. Le <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A> méthode est ensuite utilisée pour créer une nouvelle clé et l’ajouter aux paires clé/valeur.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// registry_write.cpp  
// compile with: /clr  
using namespace System;  
using namespace Microsoft::Win32;  
  
int main()  
{  
   // The second OpenSubKey argument indicates that  
   // the subkey should be writable.   
   RegistryKey^ rk;  
   rk  = Registry::CurrentUser->OpenSubKey("Software", true);  
   if (!rk)  
   {  
      Console::WriteLine("Failed to open CurrentUser/Software key");  
      return -1;  
   }  
  
   RegistryKey^ nk = rk->CreateSubKey("NewRegKey");  
   if (!nk)  
   {  
      Console::WriteLine("Failed to create 'NewRegKey'");  
      return -1;  
   }  
  
   String^ newValue = "NewValue";  
   try  
   {  
      nk->SetValue("NewKey", newValue);  
      nk->SetValue("NewKey2", 44);  
   }  
   catch (Exception^)  
   {  
      Console::WriteLine("Failed to set new values in 'NewRegKey'");  
      return -1;  
   }  
  
   Console::WriteLine("New key created.");  
   Console::Write("Use REGEDIT.EXE to verify ");  
   Console::WriteLine("'CURRENTUSER/Software/NewRegKey'\n");  
   return 0;  
}  
```  
  
### <a name="remarks"></a>Notes  
 Vous pouvez utiliser le .NET Framework pour accéder au Registre avec le <xref:Microsoft.Win32.Registry> et [RegistryKey](https://msdn.microsoft.com/library/microsoft.win32.registrykey.aspx) classes, qui sont tous deux définis dans le <xref:Microsoft.Win32> espace de noms. Le **Registre** classe est un conteneur pour les instances statiques de la <xref:Microsoft.Win32.RegistryKey> classe. Chaque instance représente un nœud de Registre racine. Les instances sont <xref:Microsoft.Win32.Registry.ClassesRoot>, <xref:Microsoft.Win32.Registry.CurrentConfig>, <xref:Microsoft.Win32.Registry.CurrentUser>, <xref:Microsoft.Win32.Registry.LocalMachine>, et <xref:Microsoft.Win32.Registry.Users>.  

## <a name="related-sections"></a>Rubriques connexes  
 <xref:System.Environment>  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
