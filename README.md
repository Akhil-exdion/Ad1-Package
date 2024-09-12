pip install <wheel file>

## How to use
import logging
from adService import service
from adService import service, service_interface

logger = logging.getLogger(__name__)
logging.basicConfig(level=logging.INFO)

# Document information
doc_info = service_interface.DocInfo(
    file_path=r'document path',
    lob='example_lob',job_id='3434366546',doc_id='68f279c2-9d35-44e6-76r676-876t8t7',es_hosts=[])

reader = service.ConcreteDocReader(doc_info.file_path)  # Your implementation of DocInterface
output_connector = service.MyConnector()
output_filter = service.SimpleFilter()
event_handler = service.AdExtraction(logger)
event_handler.process_document(doc_info, reader, output_connector, output_filter)
