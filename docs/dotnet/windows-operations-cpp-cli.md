---
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
ms.openlocfilehash: 99fce804ad30e01bdbaa99b1636a5238ff535f8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371773"
---
# <a name="windows-operations-ccli"></a>Opérations Windows (C++/CLI)

Démontre diverses tâches spécifiques à Windows à l’aide du SDK Windows.

Les sujets suivants démontrent diverses opérations Windows effectuées avec le Windows SDK à l’aide de Visual C.

## <a name="determine-if-shutdown-has-started"></a><a name="determine_shutdown"></a>Déterminer si l’arrêt a commencé

L’exemple de code suivant montre comment déterminer si l’application ou le cadre .NET est en train de se terminer. Ceci est utile pour accéder aux éléments statiques dans le cadre .NET parce que, pendant l’arrêt, ces constructions sont finalisées par le système et ne peuvent pas être utilisées de manière fiable. En vérifiant la propriété d’abord, <xref:System.Environment.HasShutdownStarted%2A> vous pouvez éviter les défaillances potentielles en n’accédant pas à ces éléments.

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

## <a name="determine-the-user-interactive-state"></a><a name="determine_user"></a>Déterminer l’état interactif de l’utilisateur

L’exemple de code suivant montre comment déterminer si le code est exécuté dans un contexte utilisateur-interactif. Si <xref:System.Environment.UserInteractive%2A> elle est fausse, alors le code fonctionne comme un processus de service ou de l’intérieur d’une application Web, auquel cas vous ne devriez pas essayer d’interagir avec l’utilisateur.

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

## <a name="read-data-from-the-windows-registry"></a><a name="read_registry"></a>Lire les données du Registre Windows

L’exemple de <xref:Microsoft.Win32.Registry.CurrentUser> code suivant utilise la clé pour lire les données du registre Windows. Tout d’abord, les sous-clés <xref:Microsoft.Win32.RegistryKey.GetSubKeyNames%2A> sont énumérées en utilisant la <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> méthode, puis le sous-clé Identities est ouvert en utilisant la méthode. Comme les touches de racine, chaque <xref:Microsoft.Win32.RegistryKey> sous-clé est représenté par la classe. Enfin, le <xref:Microsoft.Win32.RegistryKey> nouvel objet est utilisé pour énumérer les paires de clés/valeur.

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

La <xref:Microsoft.Win32.Registry> classe est simplement un <xref:Microsoft.Win32.RegistryKey>conteneur pour les instances statiques de . Chaque instance représente un nœud de registre des racines. Les instances <xref:Microsoft.Win32.Registry.ClassesRoot> <xref:Microsoft.Win32.Registry.CurrentConfig>sont <xref:Microsoft.Win32.Registry.CurrentUser> <xref:Microsoft.Win32.Registry.LocalMachine>, <xref:Microsoft.Win32.Registry.Users>, , et .

En plus d’être statiques, les objets de la <xref:Microsoft.Win32.Registry> classe sont lus uniquement. En outre, <xref:Microsoft.Win32.RegistryKey> les instances de la classe qui sont créées pour accéder au contenu des objets de registre sont également lues uniquement. Pour un exemple de la façon de remplacer ce comportement, voir [Comment : Écrire des données au Registre Windows (CMD/CLI)](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md).

Il ya deux objets <xref:Microsoft.Win32.Registry> supplémentaires <xref:Microsoft.Win32.Registry.DynData> <xref:Microsoft.Win32.Registry.PerformanceData>dans la classe: et . Les deux sont <xref:Microsoft.Win32.RegistryKey> des cas de la classe. L’objet <xref:Microsoft.Win32.Registry.DynData> contient des informations de registre dynamique, qui ne sont pris en charge que dans Windows 98 et Windows Me. L’objet <xref:Microsoft.Win32.Registry.PerformanceData> peut être utilisé pour accéder aux informations de compteur de performances pour les applications qui utilisent le système de surveillance des performances Windows. Le <xref:Microsoft.Win32.Registry.PerformanceData> nœud représente des informations qui ne sont pas réellement stockées dans le registre et ne peuvent donc pas être consultées à l’aide de Regedit.exe.

## <a name="read-windows-performance-counters"></a><a name="read_performance"></a>Lire Windows Performance Counters

Certaines applications et sous-systèmes Windows exposent les données de performance via le système de performances Windows. Ces compteurs peuvent être <xref:System.Diagnostics.PerformanceCounterCategory> consultés à l’aide de la et <xref:System.Diagnostics.PerformanceCounter> des classes, qui résident dans l’espace nom. <xref:System.Diagnostics?displayProperty=fullName>

L’exemple de code suivant utilise ces classes pour récupérer et afficher un compteur qui est mis à jour par Windows pour indiquer le pourcentage de temps que le processeur est occupé.

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

## <a name="retrieve-text-from-the-clipboard"></a><a name="retrieve_text"></a>Récupérer le texte du Clipboard

L’exemple de <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> code suivant utilise la <xref:System.Windows.Forms.IDataObject> fonction du membre pour renvoyer un pointeur à l’interface. Cette interface peut ensuite être interrogée pour le format des données et utilisée pour récupérer les données réelles.

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

## <a name="retrieve-the-current-username"></a><a name="retrieve_current"></a>Récupérer le nom d’utilisateur actuel

L’exemple de code suivant montre la récupération du nom d’utilisateur actuel (le nom de l’utilisateur connecté à Windows). Le nom est <xref:System.Environment.UserName%2A> stocké dans la chaîne, qui est définie dans l’espace nom. <xref:System.Environment>

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

## <a name="retrieve-the-net-framework-version"></a><a name="retrieve_dotnet"></a>Récupérer la version cadre .NET

L’exemple de code suivant montre comment déterminer la version <xref:System.Environment.Version%2A> du cadre .NET actuellement <xref:System.Version> installé avec la propriété, qui est un pointeur à un objet qui contient les informations de version.

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

## <a name="retrieve-the-local-machine-name"></a><a name="retrieve_local"></a>Récupérer le nom de la machine locale

L’exemple de code suivant montre la récupération du nom de la machine locale (le nom de l’ordinateur tel qu’il apparaît sur un réseau). Vous pouvez accomplir cela <xref:System.Environment.MachineName%2A> en obtenant la <xref:System.Environment> chaîne, qui est définie dans l’espace de nom.

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

## <a name="retrieve-the-windows-version"></a><a name="retrieve_version"></a>Récupérer la version Windows

L’exemple de code suivant montre comment récupérer les informations de la plate-forme et de la version du système d’exploitation actuel. Ces informations sont <xref:System.Environment.OSVersion%2A?displayProperty=fullName> stockées dans la propriété et se compose d’un recensement <xref:System.Environment.Version%2A> qui décrit la version de Windows en termes généraux et un objet qui contient la construction exacte du système d’exploitation.

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

## <a name="retrieve-time-elapsed-since-startup"></a><a name="retrieve_time"></a>Récupérer le temps écoulé depuis le démarrage

L’exemple de code suivant montre comment déterminer le nombre de tiques, ou le nombre de millisecondes qui se sont écoulées depuis le début de Windows. Cette valeur est <xref:System.Environment.TickCount%2A?displayProperty=fullName> stockée dans le membre et, parce qu’il s’agit d’une valeur 32 bits, se réinitialise à zéro environ tous les 24,9 jours.

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

## <a name="store-text-in-the-clipboard"></a><a name="store_text"></a>Conserver le texte dans le Clipboard

L’exemple de <xref:System.Windows.Forms.Clipboard> code suivant <xref:System.Windows.Forms> utilise l’objet défini dans l’espace nom pour stocker une chaîne. Cet objet fournit deux <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> fonctions de membre : et <xref:System.Windows.Forms.Clipboard.GetDataObject%2A>. Les données sont stockées dans le <xref:System.Object> Clipboard en envoyant tout objet dérivé de <xref:System.Windows.Forms.Clipboard.SetDataObject%2A>.

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

## <a name="write-data-to-the-windows-registry"></a><a name="write_data"></a>Écrire des données au Registre Windows

L’exemple de <xref:Microsoft.Win32.Registry.CurrentUser> code suivant utilise la clé <xref:Microsoft.Win32.RegistryKey> pour créer un exemple exécutable de la classe correspondant à la clé **logicielle.** La <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A> méthode est ensuite utilisée pour créer une nouvelle clé et ajouter aux paires de clés/valeur.

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

Vous pouvez utiliser le cadre .NET <xref:Microsoft.Win32.Registry> pour <xref:Microsoft.Win32.RegistryKey> accéder au registre avec <xref:Microsoft.Win32> les classes et les classes, qui sont toutes deux définies dans l’espace nom. La classe **d’enregistrement** est un <xref:Microsoft.Win32.RegistryKey> conteneur pour les instances statiques de la classe. Chaque instance représente un nœud de registre des racines. Les instances <xref:Microsoft.Win32.Registry.ClassesRoot> <xref:Microsoft.Win32.Registry.CurrentConfig>sont <xref:Microsoft.Win32.Registry.CurrentUser> <xref:Microsoft.Win32.Registry.LocalMachine>, <xref:Microsoft.Win32.Registry.Users>, , et .

## <a name="related-sections"></a>Sections connexes

<xref:System.Environment>

## <a name="see-also"></a>Voir aussi

[.NET Programmation avec CMD/CLI (Visual CMD)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
