в DbContext:
поменять DbContext на IdentityDbContext с установкой пакета из nuget

в startUp: ConfigureServices
сначала установить Microsoft.AspNetCore.Identity.UI
services.AddDefaultIdentity<IdentityUser>().AddEntityFrameworkStores<ApplicationDbContext>();

в конце файла, перед авторизацией, добавить
app.UseAuthentication();

добавляем миграцию, ничего в таблицах пока не меня, просто не будем заполнять ненужные столбцы/потом удалим через миграцию так же
update-database

добавляем scaffolderItem на сам проект (scaffolder)
выбираем шаблон типа Identity(удостоверение)

я добавил только login и register

в app.UseEndpoints в startup добавил endpoints.MapRazorPages();

в home/_Layout перед списком в navbar добавил <partial name="_LoginPartial" />

создал класс WC(web-constant) и добавил туда две константы:
public static string adminRole = "Admin";
public static string userRole = "User";

добавли тестовые модели теста и результатов, пока пытаюсь передать туда все, что нужно