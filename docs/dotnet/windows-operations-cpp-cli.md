---
description: 'En savoir plus sur : opérations Windows (C++/CLI)'
title: Opérations Windows (C++/CLI)
ms.date: 11/04/2016
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
ms.openlocfilehash: 95fff25cb5c921272972e343dd3a85d53f909c52
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298719"
---
# <a name="windows-operations-ccli"></a>Opérations Windows (C++/CLI)

Illustre différentes tâches spécifiques à Windows à l’aide de l’SDK Windows.

Les rubriques suivantes illustrent différentes opérations Windows effectuées avec l’SDK Windows à l’aide de Visual C++.

## <a name="determine-if-shutdown-has-started"></a><a name="determine_shutdown"></a> Déterminer si l’arrêt a commencé

L’exemple de code suivant montre comment déterminer si l’application ou le .NET Framework se termine actuellement. Cela est utile pour accéder aux éléments statiques dans le .NET Framework car, pendant l’arrêt, ces constructions sont finalisées par le système et ne peuvent pas être utilisées de manière fiable. En vérifiant d' <xref:System.Environment.HasShutdownStarted%2A> abord la propriété, vous pouvez éviter les défaillances potentielles en n’accédant pas à ces éléments.

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

## <a name="determine-the-user-interactive-state"></a><a name="determine_user"></a> Déterminer l’État interactif de l’utilisateur

L’exemple de code suivant montre comment déterminer si le code est exécuté dans un contexte interactif de l’utilisateur. Si <xref:System.Environment.UserInteractive%2A> a la valeur false, le code s’exécute en tant que processus de service ou à l’intérieur d’une application Web, auquel cas vous ne devez pas tenter d’interagir avec l’utilisateur.

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

## <a name="read-data-from-the-windows-registry"></a><a name="read_registry"></a> Lire les données du Registre Windows

L’exemple de code suivant utilise la <xref:Microsoft.Win32.Registry.CurrentUser> clé pour lire les données du Registre Windows. Tout d’abord, les sous-clés sont énumérées à l’aide de la <xref:Microsoft.Win32.RegistryKey.GetSubKeyNames%2A> méthode, puis la sous-clé Identities est ouverte à l’aide de la <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> méthode. À l’instar des clés racines, chaque sous-clé est représentée par la <xref:Microsoft.Win32.RegistryKey> classe. Enfin, le nouvel <xref:Microsoft.Win32.RegistryKey> objet est utilisé pour énumérer les paires clé/valeur.

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

La <xref:Microsoft.Win32.Registry> classe est simplement un conteneur pour les instances statiques de <xref:Microsoft.Win32.RegistryKey> . Chaque instance représente un nœud de Registre racine. Les instances sont <xref:Microsoft.Win32.Registry.ClassesRoot> ,,, <xref:Microsoft.Win32.Registry.CurrentConfig> <xref:Microsoft.Win32.Registry.CurrentUser> <xref:Microsoft.Win32.Registry.LocalMachine> et <xref:Microsoft.Win32.Registry.Users> .

En plus d’être statiques, les objets de la <xref:Microsoft.Win32.Registry> classe sont en lecture seule. En outre, les instances de la <xref:Microsoft.Win32.RegistryKey> classe qui sont créées pour accéder au contenu des objets du Registre sont également en lecture seule. Pour obtenir un exemple de la façon de substituer ce comportement, consultez [Comment : écrire des données dans le Registre Windows (C++/CLI)](#write_data).

La classe contient deux objets supplémentaires <xref:Microsoft.Win32.Registry> : <xref:Microsoft.Win32.Registry.DynData> et <xref:Microsoft.Win32.Registry.PerformanceData> . Les deux sont des instances de la <xref:Microsoft.Win32.RegistryKey> classe. L' <xref:Microsoft.Win32.Registry.DynData> objet contient des informations de Registre dynamiques, qui sont uniquement prises en charge dans windows 98 et Windows Me. L' <xref:Microsoft.Win32.Registry.PerformanceData> objet peut être utilisé pour accéder aux informations de compteur de performance pour les applications qui utilisent le système d’analyse des performances Windows. Le <xref:Microsoft.Win32.Registry.PerformanceData> nœud représente des informations qui ne sont pas réellement stockées dans le registre et qui ne peuvent donc pas être affichées à l’aide de Regedit.exe.

## <a name="read-windows-performance-counters"></a><a name="read_performance"></a> Lire les compteurs de performances Windows

Certaines applications et tous les sous-systèmes Windows exposent les données de performances via le système de performances Windows. Ces compteurs sont accessibles à l’aide des <xref:System.Diagnostics.PerformanceCounterCategory> <xref:System.Diagnostics.PerformanceCounter> classes et, qui résident dans l' <xref:System.Diagnostics?displayProperty=fullName> espace de noms.

L’exemple de code suivant utilise ces classes pour récupérer et afficher un compteur mis à jour par Windows pour indiquer le pourcentage de temps pendant lequel le processeur est occupé.

> [!NOTE]
> L’exécution de cet exemple sur Windows Vista nécessite des privilèges d’administrateur.

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

## <a name="retrieve-text-from-the-clipboard"></a><a name="retrieve_text"></a> Récupérer le texte du presse-papiers

L’exemple de code suivant utilise la <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> fonction membre pour retourner un pointeur vers l' <xref:System.Windows.Forms.IDataObject> interface. Cette interface peut ensuite être interrogée pour obtenir le format des données et les utiliser pour récupérer les données réelles.

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

## <a name="retrieve-the-current-username"></a><a name="retrieve_current"></a> Récupérer le nom d’utilisateur actuel

L’exemple de code suivant montre la récupération du nom d’utilisateur actuel (nom de l’utilisateur connecté à Windows). Le nom est stocké dans la <xref:System.Environment.UserName%2A> chaîne, qui est définie dans l' <xref:System.Environment> espace de noms.

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

## <a name="retrieve-the-net-framework-version"></a><a name="retrieve_dotnet"></a> Récupérer la version de .NET Framework

L’exemple de code suivant montre comment déterminer la version du .NET Framework actuellement installé avec la <xref:System.Environment.Version%2A> propriété, qui est un pointeur vers un <xref:System.Version> objet qui contient les informations de version.

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

## <a name="retrieve-the-local-machine-name"></a><a name="retrieve_local"></a> Récupérer le nom de l’ordinateur local

L’exemple de code suivant illustre la récupération du nom de l’ordinateur local (le nom de l’ordinateur tel qu’il apparaît sur un réseau). Pour ce faire, vous pouvez obtenir la <xref:System.Environment.MachineName%2A> chaîne, qui est définie dans l' <xref:System.Environment> espace de noms.

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

## <a name="retrieve-the-windows-version"></a><a name="retrieve_version"></a> Récupérer la version de Windows

L’exemple de code suivant montre comment récupérer les informations relatives à la plateforme et à la version du système d’exploitation actuel. Ces informations sont stockées dans la <xref:System.Environment.OSVersion%2A?displayProperty=fullName> propriété et se composent d’une énumération qui décrit la version de Windows en termes larges et un <xref:System.Environment.Version%2A> objet qui contient la build exacte du système d’exploitation.

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

## <a name="retrieve-time-elapsed-since-startup"></a><a name="retrieve_time"></a> Récupérer le temps écoulé depuis le démarrage

L’exemple de code suivant montre comment déterminer le nombre de cycles, ou le nombre de millisecondes qui se sont écoulées depuis le démarrage de Windows. Cette valeur est stockée dans le <xref:System.Environment.TickCount%2A?displayProperty=fullName> membre et, étant donné qu’il s’agit d’une valeur 32 bits, réinitialise à zéro tous les 24,9 jours environ.

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

## <a name="store-text-in-the-clipboard"></a><a name="store_text"></a> Stocker du texte dans le presse-papiers

L’exemple de code suivant utilise l' <xref:System.Windows.Forms.Clipboard> objet défini dans l' <xref:System.Windows.Forms> espace de noms pour stocker une chaîne. Cet objet fournit deux fonctions membres : <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> et <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> . Les données sont stockées dans le presse-papiers en envoyant tout objet dérivé de <xref:System.Object> à <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> .

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

## <a name="write-data-to-the-windows-registry"></a><a name="write_data"></a> Écrire des données dans le Registre Windows

L’exemple de code suivant utilise la <xref:Microsoft.Win32.Registry.CurrentUser> clé pour créer une instance accessible en écriture de la <xref:Microsoft.Win32.RegistryKey> classe correspondant à la clé du **logiciel** . La <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A> méthode est ensuite utilisée pour créer une nouvelle clé et l’ajouter aux paires clé/valeur.

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

Vous pouvez utiliser la .NET Framework pour accéder au registre avec les <xref:Microsoft.Win32.Registry> <xref:Microsoft.Win32.RegistryKey> classes et, qui sont toutes les deux définies dans l' <xref:Microsoft.Win32> espace de noms. La classe **Registry** est un conteneur pour les instances statiques de la <xref:Microsoft.Win32.RegistryKey> classe. Chaque instance représente un nœud de Registre racine. Les instances sont <xref:Microsoft.Win32.Registry.ClassesRoot> ,,, <xref:Microsoft.Win32.Registry.CurrentConfig> <xref:Microsoft.Win32.Registry.CurrentUser> <xref:Microsoft.Win32.Registry.LocalMachine> et <xref:Microsoft.Win32.Registry.Users> .

## <a name="related-sections"></a>Sections connexes

<xref:System.Environment>

## <a name="see-also"></a>Voir aussi

[Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
