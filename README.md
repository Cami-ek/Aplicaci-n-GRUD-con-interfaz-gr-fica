< Aplicación  x : Clase = " Biblioteca.Autores.Aplicación "
             xmlns = " http://schemas.microsoft.com/winfx/2006/xaml/presentation "
             xmlns : x = " http://schemas.microsoft.com/winfx/2006/xaml "
             xmlns : local = " clr-espacio de nombres: Biblioteca. Autores "
             StartupUri = " VentanaPrincipal.xaml " >
    < Aplicación .Recursos>

    </ Aplicación .Recursos>
</ Aplicación >
 17  Biblioteca.Autores/App.xaml.cs 
@@ -0,0 +1,17 @@
utilizando el  sistema ;
utilizando el  sistema . Colecciones . genérico ;
utilizando el  sistema . Configuración ;
utilizando el  sistema . datos ;
utilizando el  sistema . Linq ;
utilizando el  sistema . Threading . tareas ;
utilizando el  sistema . ventanas ;

 Biblioteca de espacios de nombres . Autores
{
    /// < resumen >
    /// Lógica de interacción para App.xaml
    /// </ resumen >
     Aplicación de clase parcial  pública : Aplicación 
    {
    }
}
 10  Biblioteca.Autores/AssemblyInfo.cs 
@@ -0,0 +1,10 @@
utilizando el  sistema . ventanas ;

[ montaje : ThemeInfo (
    ResourceDictionaryLocation . Ninguno , // donde se encuentran los diccionarios de recursos específicos del tema
                                     // (se usa si no se encuentra un recurso en la página,
                                     // o diccionarios de recursos de la aplicación)
    ResourceDictionaryLocation . SourceAssembly  // donde se encuentra el diccionario de recursos genéricos
                                              // (se usa si no se encuentra un recurso en la página,
                                              // aplicación, o cualquier diccionario de recursos específico del tema)
)]
 31  Library.Authors/EditAuthorWindow.xaml 
@@ -0,0 +1,31 @@
< Ventana  x : Clase = " Biblioteca.Autores.EditarVentanaDeAutor "
        xmlns = " http://schemas.microsoft.com/winfx/2006/xaml/presentation "
        xmlns : x = " http://schemas.microsoft.com/winfx/2006/xaml "
        xmlns : d = " http://schemas.microsoft.com/expression/blend/2008 "
        xmlns : mc = " http://schemas.openxmlformats.org/markup-compatibility/2006 "
        xmlns : local = " clr-espacio de nombres: Biblioteca. Autores "
        mc : Ignorable = " d "
        Título = " Editar Autor "  Alto = " 180 "  Ancho = " 300 " >
    < panel de muelle >
        < StackPanel DockPanel.Dock= " Inferior "  Orientación = " Horizontal "  HorizontalAlignment = " Centro "  Margen = " 8 " >
            < Contenido del botón  = " Guardar " Margen = " 8 " MinWidth = " 80 " Es predeterminado = " Verdadero " x : Nombre = " Guardar " Clic = " Guardar_botón_Click " />     
            < Contenido del botón  = " Cancelar " Margen = " 8 " MinWidth = " 80 " IsCancel = " True " x : Nombre = " Cancelar botón " Click = " Cancelar botón_Click " />     
        </ panel de pila >
        < Borde DockPanel.Dock= " Superior "  Margen = " 8 "  BorderBrush = " LightGray "  BorderThickness = " 1 " >
            < Margen de cuadrícula  = " 8 " >
                < Grid .Definiciones de columna >
                    < Ancho de definición de columna  = " Auto " />
                    < Definición de columna / >
                </ Grid .Definiciones de columna>
                < Grid .RowDefinitions>
                    < Altura de definición de fila  = " Auto " />
                    < Definición de Fila / >
                </ Cuadrícula .Definiciones de Fila>
                < Etiqueta Grid.Row= " 0 " Grid.Column= " 0 "  Contenido = " Nombres " />
                < TextBox Grid.Row= " 0 " Grid.Column= " 1 "  Text = " {Binding FirstName} "  VerticalAlignment = " Center "  x : Name = " FirstNameTextBox " />
                < Etiqueta Grid.Row= " 1 " Grid.Column= " 0 "  Content = " Apellidos " />
                < TextBox Grid.Row= " 1 " Grid.Column= " 1 "  Text = " {Binding LastName} "  VerticalAlignment = " Center "  x : Name = " LastNameTextBox " />
            </ Cuadrícula >
        </ Borde >
    </ panel de muelle >
</ Ventana >
 27  Library.Authors/EditAuthorWindow.xaml.cs 
@@ -0,0 +1,27 @@
utilizando el  sistema . ventanas ;
utilizando la  Biblioteca . Modelos ;
 Biblioteca de espacios de nombres . Autores
{
     clase parcial  pública EditAuthorWindow : Ventana 
    {
        public  Autor  Autor { get ; conjunto ; }
        public  EditAuthorWindow ( Autor  autor )
        {
            InitializeComponent ();
            Autor  =  autor ;
            DataContext  =  Autor ;
            FirstNameTextBox . Foco ();
            FirstNameTextBox . Seleccionar Todo ();
        }

        privado  void  SaveButton_Click ( remitente del objeto  , RoutedEventArgs e ) 
        {
            resultado del diálogo  =  verdadero ;
        }

        privado  void  CancelButton_Click ( objeto  remitente , RoutedEventArgs  e )
        {
            resultado del diálogo  =  falso ;
        }
    }
}
 13  Biblioteca.Autores/Biblioteca.Autores.csproj 
@@ -0,0 +1,13 @@
< Proyecto  Sdk = " Microsoft.NET.Sdk " >

  < Grupo de propiedades >
    < Tipo de salida >WinExe</ Tipo de salida >
    < TargetFramework >net5.0-windows</ TargetFramework >
    < UsarWPF >verdadero</ UsarWPF >
  </ grupo de propiedades >

  < Grupo de artículos >
    < ProyectoReferencia  Incluir = " ..\Library.Data\Library.Data.csproj " />
  </ Grupo de elementos >

</ Proyecto >
 27  Biblioteca.Authors/MainWindow.xaml 
@@ -0,0 +1,27 @@
< Ventana  x : Clase = " Biblioteca.Autores.VentanaPrincipal "
        xmlns = " http://schemas.microsoft.com/winfx/2006/xaml/presentation "
        xmlns : x = " http://schemas.microsoft.com/winfx/2006/xaml "
        xmlns : d = " http://schemas.microsoft.com/expression/blend/2008 "
        xmlns : mc = " http://schemas.openxmlformats.org/markup-compatibility/2006 "
        xmlns : local = " clr-espacio de nombres: Biblioteca. Autores "
        mc : Ignorable = " d "
        Título = " Biblioteca.Autores "  Alto = " 350 "  Ancho = " 400 " >
    < panel de muelle >
        < Borde DockPanel.Dock= " Inferior "  BorderBrush = " LightGray "  BorderThickness = " 1 "  Margin = " 8,4,8,8 " >
            < StackPanel  Orientación = " horizontal "  HorizontalAlignment = " centro " >
                < Contenido del botón  = " Nuevo " Margen = " 8 " MinWidth = " 80 " x : Nombre = " NewAuthorButton " Click = " NewAuthorButton_Click " />    
                < Contenido del botón  = " Modificar " Margen = " 8 " MinWidth = " 80 " x : Nombre = " ModifyAuthorButton " Click = " ModifyAuthorButton_Click " />    
                < Contenido del Botón  = " Eliminar " Margin = " 8 " MinWidth = " 80 " x : Nombre = " DeleteAuthorButton " Click = " DeleteAuthorButton_Click " />    
            </ panel de pila >
        </ Borde >
        < Borde DockPanel.Dock= " Superior "  Margen = " 8,8,8,4 "  BorderBrush = " LightGray "  BorderThickness = " 1 " >
            < DataGrid  HorizontalAlignment = " Stretch "  VerticalAlignment = " Stretch "  AutoGenerateColumns = " False "  IsReadOnly = " True "  AlternatingRowBackground = " LightBlue "  x : Name = " AuthorsDataGrid " >
                < DataGrid .Columns>
                    < DataGridTextColumn  Header = " Identidicador "  Binding = " {Binding AuthorId} " />
                    < DataGridTextColumn  Header = " Nombre de pila "  Binding = " {Binding FirstName} " />
                    < DataGridTextColumn  Header = " Apellidos "  Binding = " {Binding LastName} " />
                </ DataGrid .Columnas>
            </ Cuadrícula de datos >
        </ Borde >
    </ panel de muelle >
</ Ventana >
 70  Biblioteca.Authors/MainWindow.xaml.cs 
@@ -0,0 +1,70 @@
utilizando el  sistema . ventanas ;
utilizando la  Biblioteca . datos ;
utilizando la  Biblioteca . Modelos ;
utilizando el  sistema . Linq ;
 Biblioteca de espacios de nombres . Autores
{
     clase parcial  pública MainWindow : Ventana 
    {
         BooksDbContext  privado _contexto ;
         ventana principal pública ()
        {
            _context  =  new  BooksDbContext ();
            InitializeComponent ();
            ObtenerAutores ();
        }
         vacío  privado GetAuthors ()
        {
            AuthorsDataGrid . ItemsSource  =  _context . Autores . ALista ();
        }
         anular  privado AddAuthor ()
        {
            var  window  =  new  EditAuthorWindow ( nuevo  autor ());
            si ( ventana . ShowDialog () ==  verdadero )
            {
                _contexto . Autores . Añadir ( ventana . Autor );
                _contexto . SaveChanges ();
            }
        }
        privado  void  ModifyAuthor ( Autor  autor )
        {
            var  window  =  new  EditAuthorWindow ( autor );
            si ( ventana . ShowDialog () ==  verdadero )
            {
                _contexto . Autores . Actualizar ( autor );
                _contexto . SaveChanges ();
            }
        }
        privado  void  DeleteAuthor ( Autor  autor )
        {
            _contexto . Autores . Quitar ( autor );
            _contexto . SaveChanges ();
        }

         vacío  privado NewAuthorButton_Click ( remitente del objeto  , RoutedEventArgs e ) 
        {
            AgregarAutor ();
            ObtenerAutores ();
        }

        privado  void  ModifyAuthorButton_Click ( remitente del objeto  , RoutedEventArgs e ) 
        {
            Autor  autor  = ( Autor ) AuthorsDataGrid . ElementoSeleccionado ;
            si ( autor  ! =  nulo )
            {
                ModificarAutor ( autor );
                ObtenerAutores ();
            }
        }

        privado  void  DeleteAuthorButton_Click ( remitente del objeto  , RoutedEventArgs e ) 
        {
            Autor  autor  = ( Autor ) AuthorsDataGrid . ElementoSeleccionado ;
            si ( autor  ! =  nulo )
            {
                EliminarAutor ( autor );
                ObtenerAutores ();
            }
        }
    }
}
 45  Biblioteca.Data/BooksDbContext.cs 
@@ -0,0 +1,45 @@
utilizando el  sistema ;
utilizando  Microsoft . EntityFrameworkCore ;
utilizando la  Biblioteca . Modelos ;

 Biblioteca de espacios de nombres . Datos
{
     clase  pública BooksDbContext : DbContext
    {
        private  const  string  ConnectionString  =  @" Data Source=(localdb)\MSSQLLocalDB;Initial Catalog=Library;Integrated Security=True; "  + 
            " Tiempo de espera de conexión = 30; Cifrado = Falso; TrustServerCertificate = Falso; "  + 
            " ApplicationIntent=ReadWrite;MultiSubnetFailover=False " ;
        public  DbSet < Autor > Autores { get ; conjunto ; }
         BooksDbContext público ()
        {
            La base de datos . GarantizarCreado ();
        }
         anulación  protegida void  OnConfiguring ( DbContextOptionsBuilder  optionsBuilder )
        {
            optionsBuilder . UseSqlServer ( Cadena de conexión );
        }
         anulación  protegida void  OnModelCreating ( ModelBuilder  modelBuilder )
        {
            constructor de modelos . Entidad < Autor >(). HasData ( LoadAuthors ());
            base . OnModelCreating ( modelBuilder );
        }
         Autor privado [] LoadAuthors ()
        {
            devolver  nuevo  Autor []
            {
                nuevo  autor
                {
                    AuthorId  =  1 , Nombre  =  " Harvey " , Apellido  =  " Otoño "
                },
                nuevo  autor
                {
                    AuthorId  =  2 , Nombre  =  " Paul " , Apellido  =  " Herrera "
                },
                nuevo  autor
                {
                    AutorId  =  3 , Nombre  =  " Ian " , Apellido  =  " Summerville "
                }
            };
        }
    }
}
 15  Biblioteca.Datos/Biblioteca.Datos.csproj 
@@ -0,0 +1,15 @@
< Proyecto  Sdk = " Microsoft.NET.Sdk " >

  < Grupo de propiedades >
    < TargetFramework >net5.0</ TargetFramework >
  </ grupo de propiedades >

  < Grupo de artículos >
    < PackageReference  Incluir = " Microsoft.EntityFrameworkCore.SqlServer "  Versión = " 5.0.13 " />
  </ Grupo de elementos >

  < Grupo de artículos >
    < ProjectReference  Incluir = " .. \ \ Library.Models Library.Models.csproj " />
  </ Grupo de elementos >

</ Proyecto >
 68  Biblioteca.Modelos/Autor.cs 
@@ -0,0 +1,68 @@
utilizando el  sistema ;
utilizando el  sistema . Modelo de componente ;

 Biblioteca de espacios de nombres . Modelos
{
     clase  pública Autor : INotifyPropertyChanged
    {
         ID de autor privado int  ;
        privado  cadena  primerNombre ;
         cadena  privada apellido ;
         evento  público PropertyChangedEventHandler  PropertyChanged ;
        public  int  AuthorId
        {
            obtener  =>  autorId ;
            colocar
            {
                if ( autorId  ! =  valor )
                {
                    autorId  =  valor ;
                    OnNotifyPropertyChanged ( " AutorId " );
                }
            }
        }
         cadena  pública Nombre
        {
            get  =>  primerNombre ;
            colocar
            {
                si ( primerNombre  ! =  valor )
                {
                    nombre  =  valor ;
                    OnNotifyPropertyChanged ( " Nombre " );
                }
            }
        }
         cadena  pública Apellido
        {
            obtener  =>  apellido ;
            colocar
            {
                if ( apellido  ! =  valor )
                {
                    apellido  =  valor ;
                    OnNotifyPropertyChanged ( " Apellido " );
                }
            }
        }
         cadena  pública Nombre completo 
        {
            get  =>  $" { Nombre } { Apellido } " ;
        }
        pública  Autor ( cadena  primerNombre , cadena  lastName )
        {
            FirstName  =  firstName ;
            Apellido  =  apellido ;
        }
         Autor público (): este ( cadena . Vacío , cadena . Vacío )
        {
        }
         vacío  privado OnNotifyPropertyChanged ( string  propertyName )
        {
            si ( propiedad cambiada  ! =  nulo )
            {
                PropertyChanged ( this , new  PropertyChangedEventArgs ( propertyName ));
            }
        }
    }
}
 7  Biblioteca.Modelos/Biblioteca.Modelos.csproj 
@@ -0,0 +1,7 @@
< Proyecto  Sdk = " Microsoft.NET.Sdk " >

  < Grupo de propiedades >
    < TargetFramework >net5.0</ TargetFramework >
  </ grupo de propiedades >

</ Proyecto >
 37  Biblioteca.sln 
@@ -0,0 +1,37 @@

Archivo de solución de Microsoft Visual Studio, versión de formato 12.00
#Visual Studio Versión 16
 Versión de VisualStudio = 16.0.31911.196
 Versión mínima de VisualStudio = 10.0.40219.1
Proyecto ( "{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}" ) = "Biblioteca.Autores" , "Biblioteca.Autores\Biblioteca.Autores.csproj" , "{8DD272A8-E068-45CB-8171-89264ABB496E}"
EndProject
Proyecto ( "{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}" ) = "Biblioteca.Modelos" , "Biblioteca.Modelos\Biblioteca.Modelos.csproj" , "{07E33664-C4B8-4AA5-B97D-4D7995DDFE01}"
EndProject
Proyecto ( "{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}" ) = "Library.Data" , "Library.Data\Library.Data.csproj" , "{61DB8D03-EBAF-449A-8301-A924E0F65EBB}"
EndProject
Global
	GlobalSection ( SolutionConfigurationPlatforms ) = presolución
		Depurar| Cualquier CPU = Depurar| Cualquier CPU
		Lanzamiento| Cualquier CPU = Liberar| Cualquier CPU
	EndGlobalSection
	GlobalSection ( ProjectConfigurationPlatforms ) = postSolution
		{8DD272A8-E068-45CB-8171-89264ABB496E} . Depurar| Cualquier CPU . ActiveCfg = Depurar| Cualquier CPU
		{8DD272A8-E068-45CB-8171-89264ABB496E} . Depurar| Cualquier CPU . Construir . 0 = Depurar| Cualquier CPU
		{8DD272A8-E068-45CB-8171-89264ABB496E} . Lanzamiento| Cualquier CPU . ActiveCfg = Liberar| Cualquier CPU
		{8DD272A8-E068-45CB-8171-89264ABB496E} . Lanzamiento| Cualquier CPU . Construir . 0 = Liberar | Cualquier CPU
		{07E33664-C4B8-4AA5-B97D-4D7995DDFE01} . Depurar| Cualquier CPU . ActiveCfg = Depurar| Cualquier CPU
		{07E33664-C4B8-4AA5-B97D-4D7995DDFE01} . Depurar| Cualquier CPU . Construir . 0 = Depurar| Cualquier CPU
		{07E33664-C4B8-4AA5-B97D-4D7995DDFE01} . Lanzamiento| Cualquier CPU . ActiveCfg = Liberar| Cualquier CPU
		{07E33664-C4B8-4AA5-B97D-4D7995DDFE01} . Lanzamiento| Cualquier CPU . Construir . 0 = Liberar | Cualquier CPU
		{61DB8D03-EBAF-449A-8301-A924E0F65EBB} . Depurar| Cualquier CPU . ActiveCfg = Depurar| Cualquier CPU
		{61DB8D03-EBAF-449A-8301-A924E0F65EBB} . Depurar| Cualquier CPU . Construir . 0 = Depurar| Cualquier CPU
		{61DB8D03-EBAF-449A-8301-A924E0F65EBB} . Lanzamiento| Cualquier CPU . ActiveCfg = Liberar| Cualquier CPU
		{61DB8D03-EBAF-449A-8301-A924E0F65EBB} . Lanzamiento| Cualquier CPU . Construir . 0 = Liberar | Cualquier CPU
	EndGlobalSection
	GlobalSection ( solutionProperties ) = presolución
		HideSolutionNode =  FALSO
	EndGlobalSection
	GlobalSection ( ExtensibilityGlobals ) = postSolution
		SolutionGuid =  {6417619F-147C-4693-9955-37A7FE1379A0}
	EndGlobalSection
EndGlobal
