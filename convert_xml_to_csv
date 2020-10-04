import glob
import xml.etree.ElementTree as ET

def xml_to_csv(path, output_filename):
  xml_list = []

  with open(output_filename, "w") as train_csv_file:
      for xml_file in glob.glob(path + '/*.xml'):
          tree = ET.parse(xml_file)
          root = tree.getroot()
          full_image_name = os.path.join(IMAGE_DIR, root.find('filename').text)
          value_str_list = ' '
          for obj in root.findall('object'):

              xmlbox = obj.find('bndbox')
              x1 = int(xmlbox.find('xmin').text)
              y1 = int(xmlbox.find('ymin').text)
              x2 = int(xmlbox.find('xmax').text)
              y2 = int(xmlbox.find('ymax').text)

              class_id = 0
              value_str = ('{0},{1},{2},{3},{4}').format(x1, y1, x2, y2, class_id)
              value_str_list = value_str_list+value_str_list+' ' 

          train_csv_file.write(full_image_name+' '+ value_str+'\n')
