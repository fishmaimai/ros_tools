#!/usr/bin/env python
import rosbag
import rospy
from rostopic import get_topic_type

def remove_topic(input_file, output_file, topic_name):
    with rosbag.Bag(output_file, 'w') as outbag:
        for topic, msg, t in rosbag.Bag(input_file).read_messages():
            if topic == topic_name:
                continue 

            outbag.write(topic, msg, t)

        print("Removed topic {} from {} and saved to {}".format(topic_name, input_file, output_file))

if __name__ == '__main__':
    import sys
    if len(sys.argv) < 3:
        #print('Usage: {} <input bag> <output bag>'.format(sys.argv[0]), file=sys.stderr)
        sys.exit(1)

    input_file = sys.argv[1]
    output_file = sys.argv[2]
    topic_name = '/mff/info'

    # topic_type, _, _ = get_topic_type(input_file, topic_name)
    # if topic_type is None:
    #     #print("Topic {} not found in {}".format(topic_name, input_file), file=sys.stderr)
    #     sys.exit(2)

    remove_topic(input_file, output_file, topic_name)
