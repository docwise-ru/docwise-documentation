# Проверка файла IFC на наличие определённой группы и категорий параметров у элементов.


| IFC Entity | Property Set | Parameters |
|------------|--------------|------------|
| **IfcSpace** (Полный набор — все помещения) | RusSet_Common | RUS_MSSK_SpaceAndZone_Code, RUS_Name, RUS_MSSK_SpaceAndZone_Name |
| **IfcSpace** (Полный набор — все помещения) | RusSet_Quantities | RUS_Area |
| **IfcSpace** (Полный набор — все помещения) | RusSet_Location | RUS_Object, RUS_Object_Sub |
| **IfcSpace** (Полный набор — все помещения) | RusSet_Identification | RUS_Zone, RUS_Group_Type, RUS_Group_Number, RUS_Number |
| **IfcSpace** (Полный набор — все помещения) | RusSet_AGR | RUS_BasementFloor, RUS_GroundFloor, RUS_ResidentialRoom |
| **IfcSpace** (Исключение: RUS_Name = "СПП в ГНС") | RusSet_Common | RUS_MSSK_SpaceAndZone_Code, RUS_Name, RUS_MSSK_SpaceAndZone_Name |
| **IfcSpace** (Исключение: RUS_Name = "СПП в ГНС") | RusSet_Quantities | RUS_Area |
| **IfcSpace** (Исключение: RUS_Name = "СПП в ГНС") | RusSet_Location | RUS_Object, RUS_Object_Sub |
| **IfcSpace** (Исключение: RUS_Name = "СПП в ГНС") | RusSet_AGR | RUS_BasementFloor, RUS_GroundFloor, RUS_ResidentialRoom |
| **IfcSpace** (Исключение: RUS_Name = "Общая площадь") | RusSet_Common | RUS_MSSK_SpaceAndZone_Code, RUS_Name, RUS_MSSK_SpaceAndZone_Name |
| **IfcSpace** (Исключение: RUS_Name = "Общая площадь") | RusSet_Quantities | RUS_Area |
| **IfcSpace** (Исключение: RUS_Name = "Общая площадь") | RusSet_Location | RUS_Object, RUS_Object_Sub |
| **IfcSpace** (Исключение: RUS_Name = "Общая площадь") | RusSet_AGR | RUS_BasementFloor, RUS_GroundFloor, RUS_ResidentialRoom |
| **IfcSite** | RusSet_AGR | RUS_LandID, RUS_AreaSquare |
| **IfcCivilElement** | RusSet_Common | RUS_Name |
| **IfcCivilElement** | RusSet_Quantities | RUS_Area |
| **IfcBuilding** | RusSet_Project | RUS_ProjectName, RUS_BuildingAddress |
| **IfcBuilding** | RusSet_AGR | RUS_FNO |
| **IfcWall** | RusSet_Common | RUS_MSSK_Element_Code, RUS_Name, RUS_MSSK_Element_Name |
| **IfcWall** | RusSet_Quantities | RUS_Thickness |
| **IfcWall** | RusSet_Location | RUS_Object, RUS_Object_Sub |
| **IfcColumn** | RusSet_Common | RUS_MSSK_Element_Code, RUS_Name, RUS_MSSK_Element_Name |
| **IfcColumn** | RusSet_Quantities | RUS_Width, RUS_Height, RUS_Diameter |
| **IfcColumn** | RusSet_Location | RUS_Object, RUS_Object_Sub |
| **IfcStair** | RusSet_Common | RUS_MSSK_Element_Code, RUS_Name, RUS_MSSK_Element_Name |
| **IfcStair** | RusSet_Location | RUS_Object, RUS_Object_Sub |
| **IfcRamp** | RusSet_Common | RUS_MSSK_Element_Code, RUS_Name, RUS_MSSK_Element_Name |
| **IfcRamp** | RusSet_Quantities | RUS_Slope |
| **IfcRamp** | RusSet_Location | RUS_Object, RUS_Object_Sub |
| **IfcSlab** | RusSet_Common | RUS_MSSK_Element_Code, RUS_Name, RUS_MSSK_Element_Name |
| **IfcSlab** | RusSet_Quantities | RUS_Thickness |
| **IfcSlab** | RusSet_Location | RUS_Object, RUS_Object_Sub |
| **IfcWindow** | RusSet_Common | RUS_MSSK_Element_Code, RUS_MSSK_Material_Code, RUS_Name, RUS_MSSK_Element_Name, RUS_MSSK_Material_Name |
| **IfcWindow** | RusSet_Quantities | RUS_Width, RUS_Height, RUS_SillHeight, RUS_GlazingArea |
| **IfcWindow** | RusSet_Location | RUS_Object, RUS_Object_Sub |
| **IfcDoor** | RusSet_Common | RUS_MSSK_Element_Code, RUS_MSSK_Material_Code, RUS_Name, RUS_MSSK_Element_Name, RUS_MSSK_Material_Name |
| **IfcDoor** | RusSet_Quantities | RUS_Width, RUS_Height |
| **IfcDoor** | RusSet_Location | RUS_Object, RUS_Object_Sub |
| **IfcCurtainWall** | RusSet_Common | RUS_MSSK_Element_Code, RUS_MSSK_Material_Code, RUS_Name, RUS_MSSK_Element_Name, RUS_MSSK_Material_Name |
| **IfcCurtainWall** | RusSet_Quantities | RUS_Thickness |
| **IfcCurtainWall** | RusSet_Location | RUS_Object, RUS_Object_Sub |
| **IfcMember** | RusSet_Common | RUS_MSSK_Element_Code, RUS_MSSK_Material_Code, RUS_Name, RUS_MSSK_Material_Name |
| **IfcMember** | RusSet_Location | RUS_Object, RUS_Object_Sub |


### Объяснение

Это список требований для автоматической проверки качества информационной модели (BIM).

#### Контекст (IFC):
IfcSpace, IfcWall, IfcWindow и т.д. — это стандартные типы элементов в формате IFC.
Например, IfcWall означает, что правила ниже применяются ко всем стенам в модели.

#### Наборы свойств (Property Sets):
RusSet_Common, RusSet_Quantities — это группы параметров. Префикс "Rus" указывает на то, что это требования, разработанные специально для российских стандартов. "MSSK" в названиях параметров (например, RUS_MSSK_Element_Code) отсылает к Московским Стандартам или классификаторам строительных конструкций.

#### Параметры:
Текст в овалах (RUS_Name, RUS_Area) — это конкретные поля данных, которые обязаны быть заполнены у элемента.
Программа проверит модель и выдаст ошибку, если, например, у Стены (IfcWall) не заполнен параметр RUS_Thickness (Толщина) или RUS_Name (Имя).

#### Логика исключений (для помещений):
В начале для IfcSpace (Помещений) показана сложная логика.
По умолчанию проверяется полный набор данных (включая идентификацию RusSet_Identification).
Но если помещение называется "СПП в ГНС" или "Общая площадь", то программа переключается в режим "Укороченный набор" и не проверяет блок идентификации (на скриншоте он зачеркнут/полупрозрачен). Это сделано, потому что для технических или общих помещений не требуются детальные коды зонирования.
